---
layout: default
title: "Reproducibility Research for CS Publications"
permalink: /projects/reproducibility.html
---

# Research Artifact Reproducibility Project

<div class="project-header">
  <div class="project-header-content">
    <p class="project-subtitle">Making Computer Science Research Reproducible</p>
    <p class="project-dates"><strong>Dates:</strong> August 2023 – December 2023</p>
    <p class="project-affiliation"><strong>Affiliation:</strong> University of Illinois Urbana-Champaign, CS527</p>
  </div>
</div>

<div class="project-overview">
  <h2>Project Overview</h2>
  <p>Despite the importance of reproducibility in scientific research, many computer science publications suffer from <strong>software decay</strong>, <strong>incomplete documentation</strong>, or <strong>unavailable dependencies</strong>. This project aimed to systematically address these challenges by developing containerized environments and standardized specifications for research artifacts from top-tier computer science publications.</p>
  
  <div class="key-stats">
    <div class="stat-box">
      <span class="stat-number">26</span>
      <span class="stat-label">Research Papers</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">15+</span>
      <span class="stat-label">Successful Builds</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">2011-2024</span>
      <span class="stat-label">Publication Range</span>
    </div>
  </div>
</div>

<div class="methodology-section">
  <h2>Methodology & Technical Approach</h2>
  
  <div class="methodology-steps">
    <div class="step-card">
      <h3>1. Paper Selection & Analysis</h3>
      <p>Selected diverse papers from conferences including PLDI, OOPSLA, FSE, and others spanning from 2011 to 2024, focusing on those with available source code and computational artifacts.</p>
    </div>
    
    <div class="step-card">
      <h3>2. YAML Specification Development</h3>
      <p>Created structured YAML specifications for each paper, detailing metadata, dependencies, build instructions, and validation procedures in a standardized format.</p>
      <div class="code-snippet">
        <pre>
title: "Example Paper Title"
authors: "Author One, Author Two"
year: 2020
dblp_url: "https://dblp.org/example"
badges: ["available", "reusable"]
computational_status: "BuildAndTestSuccess"
build:
  - run: apt-get update && apt-get install -y build-essential
  - workdir: /experiment
  - run: ./configure && make
  - run: |
      cd /experiment/tests
      ./run_tests.sh
        </pre>
      </div>
    </div>
    
    <div class="step-card">
      <h3>3. Containerization Strategy</h3>
      <p>Implemented Docker containers to create isolated, reproducible environments, ensuring consistent behavior across different systems and preserving exact dependencies.</p>
    </div>
    
    <div class="step-card">
      <h3>4. Automated Build & Test</h3>
      <p>Developed automation scripts to validate YAML specifications, convert them to Dockerfiles, and execute build and test procedures consistently.</p>
    </div>
    
    <div class="step-card">
      <h3>5. Phased Evaluation</h3>
      <p>Conducted systematic evaluation through seven progressive phases, incrementally improving reproducibility and documenting challenges at each stage.</p>
    </div>
  </div>
</div>

<div class="challenges-section">
  <h2>Challenges & Solutions</h2>
  
  <div class="challenge-grid">
    <div class="challenge-card">
      <h3>Missing Dependencies</h3>
      <p><strong>Challenge:</strong> Papers like <code>FengKRR12</code> failed due to missing libraries, often with deprecated versions.</p>
      <p><strong>Solution:</strong> Implemented repository source switching and version pinning to restore compatibility with older packages.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Obsolete Build Systems</h3>
      <p><strong>Challenge:</strong> <code>LimFAK11</code> used outdated build processes incompatible with modern systems.</p>
      <p><strong>Solution:</strong> Created custom build scripts and patched Makefiles to accommodate modern compiler requirements.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Compiler Errors</h3>
      <p><strong>Challenge:</strong> <code>PrakriyaCBSC24</code> exhibited compiler errors due to language standard changes.</p>
      <p><strong>Solution:</strong> Added specific compiler flags and patches to address syntactic differences between language versions.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Network-Related Issues</h3>
      <p><strong>Challenge:</strong> <code>ShahKZ17</code> faced timeout errors while attempting to receive keys from servers.</p>
      <p><strong>Solution:</strong> Implemented retry mechanisms and alternative source repositories for dependencies.</p>
    </div>
  </div>
</div>

<div class="results-section">
  <h2>Results & Impact</h2>
  
  <div class="results-visualization">
    <div class="chart-container">
      <!-- Placeholder for a chart visualization -->
      <div class="placeholder-chart">
        <div class="chart-bar success" style="height: 60%;">
          <span class="bar-label">BuildSuccess<br>60%</span>
        </div>
        <div class="chart-bar partial" style="height: 25%;">
          <span class="bar-label">BuildOnly<br>25%</span>
        </div>
        <div class="chart-bar failure" style="height: 15%;">
          <span class="bar-label">BuildFailure<br>15%</span>
        </div>
      </div>
      <p class="chart-caption">Reproducibility Status Across All Papers</p>
    </div>
    
    <div class="results-summary">
      <ul class="achievement-list">
        <li>Successfully achieved <strong>BuildAndTestSuccess</strong> status for 15+ papers across diverse computational environments</li>
        <li>Created a comprehensive troubleshooting framework for common reproducibility challenges</li>
        <li>Demonstrated viability of containerization for long-term research preservation</li>
        <li>Developed standardized YAML specification format that can be adopted by future researchers</li>
        <li>Reconstructed working environments for papers spanning over a decade of computer science research</li>
      </ul>
    </div>
  </div>
</div>

<div class="technical-details">
  <h2>Technical Implementation Details</h2>
  
  <div class="details-tabs">
    <div class="tab-buttons">
      <button class="tab-button active" onclick="showTab('container-tab')">Containerization</button>
      <button class="tab-button" onclick="showTab('yaml-tab')">YAML Structure</button>
      <button class="tab-button" onclick="showTab('validation-tab')">Validation Process</button>
    </div>
    
    <div id="container-tab" class="tab-content active">
      <h3>Docker Containerization Strategy</h3>
      <p>Each paper was containerized using a consistent approach:</p>
      <ul>
        <li>Base images selected to match paper requirements (Ubuntu, Debian, Alpine)</li>
        <li>Multi-stage builds to minimize image size while preserving dependencies</li>
        <li>Volume mounting for test artifacts and data preservation</li>
        <li>Environment variable standardization for configuration</li>
      </ul>
      <p>This approach ensured that even papers with complex dependencies like <code>KangKSLPSKCCHY18</code> could be reliably reproduced.</p>
    </div>
    
    <div id="yaml-tab" class="tab-content">
      <h3>YAML Specification Design</h3>
      <p>The YAML structure was designed to balance human readability with machine processing:</p>
      <ul>
        <li><strong>Metadata Section:</strong> Paper identifiers, authors, publication details</li>
        <li><strong>Badges Section:</strong> Standardized reproducibility indicators</li>
        <li><strong>Build Section:</strong> Ordered list of directives for environment setup</li>
        <li><strong>Test Section:</strong> Validation procedures and expected outcomes</li>
      </ul>
      <p>This structure allowed for automated processing while maintaining flexibility for diverse research artifacts.</p>
    </div>
    
    <div id="validation-tab" class="tab-content">
      <h3>Automated Validation Process</h3>
      <p>A systematic validation pipeline was implemented:</p>
      <ol>
        <li>YAML schema validation against standardized specifications</li>
        <li>Dockerfile generation from validated YAML specifications</li>
        <li>Container build process with consistent error handling</li>
        <li>Automated test execution in ephemeral environments</li>
        <li>Result capture and standardized reporting</li>
      </ol>
      <p>This process enabled objective assessment of reproducibility status for each paper.</p>
    </div>
  </div>
</div>

<div class="lessons-learned">
  <h2>Lessons Learned & Best Practices</h2>
  
  <div class="lessons-content">
    <p>This project revealed several key insights about research reproducibility:</p>
    
    <div class="lessons-grid">
      <div class="lesson-card">
        <h4>Dependency Management</h4>
        <p>Explicit version pinning and alternative source repositories are essential for long-term reproducibility.</p>
      </div>
      
      <div class="lesson-card">
        <h4>Build Isolation</h4>
        <p>Containerization significantly improves reproducibility by eliminating system-specific dependencies.</p>
      </div>
      
      <div class="lesson-card">
        <h4>Documentation Quality</h4>
        <p>Detailed build and test instructions are as important as the code itself for research artifacts.</p>
      </div>
      
      <div class="lesson-card">
        <h4>Standardization</h4>
        <p>Common formats for specifying research environments facilitate validation and long-term preservation.</p>
      </div>
    </div>
  </div>
</div>

<div class="skills-section">
  <h2>Skills & Technologies</h2>
  
  <div class="skills-grid">
    <div class="skill-category">
      <h3>Containerization</h3>
      <ul>
        <li>Docker</li>
        <li>Container orchestration</li>
        <li>Multi-stage builds</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Build Systems</h3>
      <ul>
        <li>Make/CMake</li>
        <li>Autotools</li>
        <li>Package managers</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Languages</h3>
      <ul>
        <li>Python</li>
        <li>Bash</li>
        <li>YAML</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Methods</h3>
      <ul>
        <li>Software archaeology</li>
        <li>Reproducible research</li>
        <li>Technical documentation</li>
      </ul>
    </div>
  </div>
</div>

<div class="resources-section">
  <h2>Resources & Links</h2>
  
  <div class="resources-grid">
    <a href="https://gitlab.engr.illinois.edu/yuxuanm4/cs527" class="resource-card">
      <h3>📁 GitLab Repository</h3>
      <p>Access the complete project codebase</p>
    </a>
    
    <a href="/troubleshooting-guide.html" class="resource-card">
      <h3>🛠️ Troubleshooting Guide</h3>
      <p>Solutions to common reproducibility challenges</p>
    </a>
  </div>
</div>

<style>
/* Overall styling */
.project-header {
  background-color: #f8f9fa;
  padding: 20px;
  border-radius: 8px;
  margin-bottom: 30px;
}

.project-subtitle {
  font-size: 1.2em;
  color: #666;
  margin-bottom: 10px;
}

.project-overview {
  margin-bottom: 40px;
}

/* Key stats styling */
.key-stats {
  display: flex;
  justify-content: space-between;
  margin: 30px 0;
  flex-wrap: wrap;
}

.stat-box {
  background-color: #f0f7ff;
  border-radius: 8px;
  padding: 20px;
  text-align: center;
  flex: 1;
  margin: 0 10px;
  min-width: 150px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.stat-number {
  display: block;
  font-size: 2em;
  font-weight: bold;
  color: #0066cc;
  margin-bottom: 5px;
}

.stat-label {
  color: #555;
}

/* Methodology section */
.methodology-steps {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-top: 20px;
}

.step-card {
  background-color: #fff;
  border-left: 4px solid #3498db;
  padding: 15px;
  border-radius: 0 8px 8px 0;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.step-card h3 {
  color: #3498db;
  margin-top: 0;
}

/* Code snippet */
.code-snippet {
  background-color: #f8f8f8;
  border-radius: 4px;
  padding: 10px;
  overflow-x: auto;
  margin: 15px 0;
  font-family: monospace;
  font-size: 0.9em;
}

.code-snippet pre {
  margin: 0;
  white-space: pre-wrap;
}

/* Challenges section */
.challenge-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.challenge-card {
  background-color: #fff;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.challenge-card h3 {
  color: #e74c3c;
  margin-top: 0;
}

/* Results section */
.results-visualization {
  display: flex;
  flex-wrap: wrap;
  gap: 30px;
  margin-top: 20px;
}

.chart-container {
  flex: 1;
  min-width: 300px;
}

.placeholder-chart {
  height: 300px;
  background-color: #f9f9f9;
  border-radius: 8px;
  display: flex;
  align-items: flex-end;
  justify-content: center;
  padding: 20px;
  gap: 30px;
}

.chart-bar {
  width: 80px;
  border-radius: 8px 8px 0 0;
  position: relative;
  display: flex;
  justify-content: center;
}

.bar-label {
  position: absolute;
  bottom: -30px;
  text-align: center;
  font-size: 0.8em;
  color: #333;
}

.success {
  background-color: #2ecc71;
}

.partial {
  background-color: #f39c12;
}

.failure {
  background-color: #e74c3c;
}

.chart-caption {
  text-align: center;
  color: #666;
  font-style: italic;
  margin-top: 40px;
}

.results-summary {
  flex: 1;
  min-width: 300px;
}

.achievement-list li {
  margin-bottom: 10px;
}

/* Technical details tabs */
.details-tabs {
  margin-top: 20px;
}

.tab-buttons {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}

.tab-button {
  padding: 10px 15px;
  background-color: #f1f1f1;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.tab-button.active {
  background-color: #3498db;
  color: white;
}

.tab-content {
  display: none;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
}

.tab-content.active {
  display: block;
}

/* Lessons learned */
.lessons-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.lesson-card {
  background-color: #f5f5f5;
  border-radius: 8px;
  padding: 15px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}

.lesson-card h4 {
  color: #2c3e50;
  margin-top: 0;
}

/* Skills section */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.skill-category {
  background-color: #f8f9fa;
  border-radius: 8px;
  padding: 15px;
}

.skill-category h3 {
  color: #3498db;
  margin-top: 0;
  font-size: 1.1em;
  border-bottom: 1px solid #ddd;
  padding-bottom: 8px;
  margin-bottom: 10px;
}

.skill-category ul {
  padding-left: 20px;
  margin: 0;
}

.skill-category li {
  margin-bottom: 5px;
}

/* Resources section */
.resources-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.resource-card {
  background-color: #f8f9fa;
  border-radius: 8px;
  padding: 20px;
  text-decoration: none;
  color: inherit;
  transition: transform 0.3s, box-shadow 0.3s;
  display: block;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.resource-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

.resource-card h3 {
  margin-top: 0;
  color: #2c3e50;
}

.resource-card p {
  color: #666;
  margin-bottom: 0;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .key-stats, .challenge-grid, .results-visualization, 
  .lessons-grid, .skills-grid, .resources-grid {
    grid-template-columns: 1fr;
  }
  
  .stat-box {
    margin: 10px 0;
  }
}
</style>

<script>
function showTab(tabId) {
  // Hide all tabs
  const tabs = document.getElementsByClassName('tab-content');
  for (let i = 0; i < tabs.length; i++) {
    tabs[i].classList.remove('active');
  }
  
  // Remove active class from all buttons
  const buttons = document.getElementsByClassName('tab-button');
  for (let i = 0; i < buttons.length; i++) {
    buttons[i].classList.remove('active');
  }
  
  // Show the selected tab
  document.getElementById(tabId).classList.add('active');
  
  // Make the clicked button active
  const activeButton = document.querySelector(`button[onclick="showTab('${tabId}')"]`);
  activeButton.classList.add('active');
}
</script>


