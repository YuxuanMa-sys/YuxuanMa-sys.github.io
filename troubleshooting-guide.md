---
layout: default
title: "Research Reproducibility Troubleshooting Guide"
permalink: /troubleshooting-guide.html
---

# Research Reproducibility Troubleshooting Guide

<div class="guide-header">
  <p class="guide-subtitle">Common Issues and Solutions for Research Artifact Reproduction</p>
</div>

## Common Reproducibility Issues and Solutions

This guide addresses frequently encountered problems when attempting to reproduce research artifacts from computer science publications. Below are categorized issues with detailed solutions and workarounds.

### Dependency Resolution Problems

<div class="issue-card">
  <div class="issue-header">
    <h3>🔍 Missing or Deprecated Package Repositories</h3>
    <span class="severity high">High Severity</span>
  </div>
  <div class="issue-content">
    <p><strong>Symptoms:</strong> Build fails with errors like "404 Not Found" when accessing package repositories, or "Package not found in repository".</p>
    
    <p><strong>Example Error:</strong></p>
    <div class="code-block">
      <pre>E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/libpng/libpng12-0_1.2.54-1ubuntu1_amd64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?</pre>
    </div>
    
    <p><strong>Solution:</strong></p>
    <ol>
      <li>Use the Wayback Machine to locate archived versions of packages</li>
      <li>Switch to legacy package repositories in your sources.list</li>
      <li>Add the following to your container setup:</li>
    </ol>
    
    <div class="code-block">
      <pre>RUN echo "deb http://old-releases.ubuntu.com/ubuntu/ trusty main restricted universe multiverse" > /etc/apt/sources.list
RUN echo "deb http://old-releases.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse" >> /etc/apt/sources.list
RUN apt-get update</pre>
    </div>
  </div>
</div>

<div class="issue-card">
  <div class="issue-header">
    <h3>🧰 Conflicting Dependency Versions</h3>
    <span class="severity medium">Medium Severity</span>
  </div>
  <div class="issue-content">
    <p><strong>Symptoms:</strong> Library load errors, undefined symbol references, or segmentation faults during runtime.</p>
    
    <p><strong>Example Error:</strong></p>
    <div class="code-block">
      <pre>ImportError: /usr/local/lib/python3.6/dist-packages/numpy/core/_multiarray_umath.cpython-36m-x86_64-linux-gnu.so: 
undefined symbol: PyFPE_jbuf</pre>
    </div>
    
    <p><strong>Solution:</strong></p>
    <ol>
      <li>Create isolated environments using virtual environments or containers</li>
      <li>Pin exact dependency versions in requirements files</li>
      <li>Use dependency resolution tools:</li>
    </ol>
    
    <div class="code-block">
      <pre># In your Dockerfile or setup script:
RUN pip install pip-tools
COPY requirements.in .
RUN pip-compile requirements.in --output-file requirements.txt
RUN pip install -r requirements.txt</pre>
    </div>
  </div>
</div>

### Build System Issues

<div class="issue-card">
  <div class="issue-header">
    <h3>🏗️ Obsolete Build Tools</h3>
    <span class="severity high">High Severity</span>
  </div>
  <div class="issue-content">
    <p><strong>Symptoms:</strong> Build fails with errors like "This package requires autoconf 2.13" or "Unsupported compiler version".</p>
    
    <p><strong>Example Error:</strong></p>
    <div class="code-block">
      <pre>configure.ac:15: error: Autoconf version 2.69 or higher is required
configure.ac:15: the top level</pre>
    </div>
    
    <p><strong>Solution:</strong></p>
    <ol>
      <li>Install and use specific versions of build tools through version managers</li>
      <li>For autotools, use the following approach:</li>
    </ol>
    
    <div class="code-block">
      <pre>RUN cd /tmp && \
    wget https://ftp.gnu.org/gnu/autoconf/autoconf-2.69.tar.gz && \
    tar xzf autoconf-2.69.tar.gz && \
    cd autoconf-2.69 && \
    ./configure && make && make install</pre>
    </div>
  </div>
</div>

<div class="issue-card">
  <div class="issue-header">
    <h3>📝 Makefile Syntax Changes</h3>
    <span class="severity medium">Medium Severity</span>
  </div>
  <div class="issue-content">
    <p><strong>Symptoms:</strong> Make fails with syntax errors or unexpected behavior in newer versions.</p>
    
    <p><strong>Example Error:</strong></p>
    <div class="code-block">
      <pre>Makefile:37: *** missing separator.  Stop.</pre>
    </div>
    
    <p><strong>Solution:</strong></p>
    <ol>
      <li>Check for tab vs. space indentation (common issue)</li>
      <li>Apply this patch to fix common Makefile issues:</li>
    </ol>
    
    <div class="code-block">
      <pre>RUN sed -i 's/[[:space:]]\+$//' Makefile
RUN sed -i 's/^[[:space:]]\+/\t/' Makefile</pre>
    </div>
  </div>
</div>

### Language and Compiler Issues

<div class="issue-card">
  <div class="issue-header">
    <h3>💻 Language Standard Changes</h3>
    <span class="severity high">High Severity</span>
  </div>
  <div class="issue-content">
    <p><strong>Symptoms:</strong> Compiler errors about deprecated features, invalid syntax, or missing includes.</p>
    
    <p><strong>Example Error:</strong></p>
    <div class="code-block">
      <pre>error: 'auto_ptr' is deprecated [-Werror=deprecated-declarations]
std::auto_ptr<MyClass> ptr(new MyClass());</pre>
    </div>
    
    <p><strong>Solution:</strong></p>
    <ol>
      <li>Explicitly specify language standards in compiler flags</li>
      <li>Modify compiler flags in Makefiles or build scripts:</li>
    </ol>
    
    <div class="code-block">
      <pre>RUN sed -i 's/CXXFLAGS =/CXXFLAGS = -std=c++11 -Wno-deprecated-declarations /' Makefile</pre>
    </div>
  </div>
</div>

### Runtime Environment Issues

<div class="issue-card">
  <div class="issue-header">
    <h3>📂 File Path Assumptions</h3>
    <span class="severity low">Low Severity</span>
  </div>
  <div class="issue-content">
    <p><strong>Symptoms:</strong> "File not found" errors despite files being present, or incorrect relative path handling.</p>
    
    <p><strong>Example Error:</strong></p>
    <div class="code-block">
      <pre>FileNotFoundError: [Errno 2] No such file or directory: './data/input.txt'</pre>
    </div>
    
    <p><strong>Solution:</strong></p>
    <ol>
      <li>Create symbolic links to maintain expected directory structures</li>
      <li>Modify source code to accept configurable paths</li>
      <li>Use environment variables to control file paths:</li>
    </ol>
    
    <div class="code-block">
      <pre>RUN mkdir -p /data
ENV DATA_DIR=/data
RUN ln -s /data ./data</pre>
    </div>
  </div>
</div>

<div class="issue-card">
  <div class="issue-header">
    <h3>⏱️ Timeouts and Rate Limits</h3>
    <span class="severity medium">Medium Severity</span>
  </div>
  <div class="issue-content">
    <p><strong>Symptoms:</strong> Building or running fails due to API rate limits or network timeouts.</p>
    
    <p><strong>Example Error:</strong></p>
    <div class="code-block">
      <pre>Error: Unable to download from 'https://api.github.com': TCP timeout after 60s</pre>
    </div>
    
    <p><strong>Solution:</strong></p>
    <ol>
      <li>Implement retry logic with exponential backoff</li>
      <li>Cache downloaded resources locally</li>
      <li>Use the following wrapper for network operations:</li>
    </ol>
    
    <div class="code-block">
      <pre>#!/bin/bash
# retry.sh - Retry a command up to 5 times with exponential backoff
max_attempts=5
attempt=1
until "$@"; do
  if [ $attempt -eq $max_attempts ]; then
    echo "Command failed after $max_attempts attempts: $@"
    exit 1
  fi
  sleep_time=$((2**attempt))
  echo "Command failed, retrying in ${sleep_time}s..."
  sleep $sleep_time
  attempt=$((attempt+1))
done</pre>
    </div>
  </div>
</div>

## Best Practices for Reproducibility

<div class="best-practices">
  <ul>
    <li><strong>Document Everything:</strong> Record all steps, including errors and workarounds</li>
    <li><strong>Version Pin Everything:</strong> Specify exact versions for all dependencies</li>
    <li><strong>Automate Setup:</strong> Create scripts for environment setup and verification</li>
    <li><strong>Containerize:</strong> Use Docker to isolate and preserve environments</li>
    <li><strong>Test Incrementally:</strong> Validate each component individually before integration</li>
  </ul>
</div>

<style>
  .guide-header {
    background-color: #f8f9fa;
    padding: 20px;
    border-radius: 8px;
    margin-bottom: 30px;
  }
  
  .guide-subtitle {
    font-size: 1.2em;
    color: #666;
    margin-bottom: 10px;
  }
  
  .issue-card {
    background-color: #fff;
    border-radius: 8px;
    padding: 0;
    margin-bottom: 30px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    overflow: hidden;
  }
  
  .issue-header {
    padding: 15px 20px;
    background-color: #f8f9fa;
    border-bottom: 1px solid #eee;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .issue-header h3 {
    margin: 0;
    color: #333;
  }
  
  .severity {
    padding: 4px 8px;
    border-radius: 4px;
    font-size: 0.8em;
    font-weight: bold;
  }
  
  .high {
    background-color: #ffebee;
    color: #c62828;
  }
  
  .medium {
    background-color: #fff8e1;
    color: #ff8f00;
  }
  
  .low {
    background-color: #e8f5e9;
    color: #388e3c;
  }
  
  .issue-content {
    padding: 20px;
  }
  
  .code-block {
    background-color: #f5f5f5;
    border-radius: 4px;
    padding: 15px;
    overflow-x: auto;
    margin: 15px 0;
  }
  
  .code-block pre {
    margin: 0;
    font-family: monospace;
    font-size: 0.9em;
  }
  
  .best-practices {
    background-color: #e8f5e9;
    border-radius: 8px;
    padding: 20px;
    margin-top: 30px;
  }
  
  .best-practices ul {
    margin: 0;
    padding-left: 25px;
  }
  
  .best-practices li {
    margin-bottom: 10px;
  }
  
  @media (max-width: 768px) {
    .issue-header {
      flex-direction: column;
      align-items: flex-start;
    }
    
    .severity {
      margin-top: 10px;
    }
  }
</style> 