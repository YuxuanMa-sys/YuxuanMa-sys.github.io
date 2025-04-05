---
layout: default
title: "Enhancing Code Reasoning and Test Generation in DeepSeekCoder (Python)"
---

<style>
  .project-container {
    max-width: 900px;
    margin: 0 auto;
    padding: 1rem;
  }
  .challenge-solution {
    display: flex;
    margin-bottom: 2rem;
    gap: 2rem;
  }
  .challenge-solution div {
    flex: 1;
  }
  .challenge {
    background-color: #f8f9fa;
    padding: 1rem;
    border-left: 4px solid #e74c3c;
    border-radius: 4px;
  }
  .solution {
    background-color: #f8f9fa;
    padding: 1rem;
    border-left: 4px solid #2ecc71;
    border-radius: 4px;
  }
  .metrics-container {
    display: flex;
    justify-content: space-between;
    margin: 2rem 0;
    text-align: center;
  }
  .metric {
    flex: 1;
    padding: 1rem;
    background-color: #f8f9fa;
    border-radius: 8px;
    margin: 0 0.5rem;
  }
  .metric-value {
    font-size: 2.5rem;
    color: #3498db;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }
  .metric-label {
    font-size: 1rem;
    color: #7f8c8d;
  }
  .image-gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
    margin: 2rem 0;
  }
  .gallery-item {
    flex: 1;
    min-width: 250px;
    max-width: 400px;
    text-align: center;
  }
  .gallery-item img {
    width: 100%;
    border-radius: 8px;
    border: 1px solid #ddd;
  }
  .gallery-caption {
    margin-top: 0.5rem;
    font-size: 0.9rem;
    color: #555;
  }
</style>

<div class="project-container">
  <h1>Enhancing Code Reasoning and Test Generation in DeepSeekCoder</h1>
  
  <p class="project-meta">
    <strong>Dates:</strong> August 2024 – December 2024<br>
    <strong>Affiliation:</strong> University of Illinois Urbana-Champaign<br>
    <strong>Team Size:</strong> 4 members
  </p>

  <h2>Project Overview</h2>
  <p>
    We addressed the challenge of limited accuracy in code reasoning and test generation by exploring how <strong>tailored prompts</strong> can guide large language models to produce syntactically correct and logically accurate outputs. This research used DeepSeekCoder, a 7B parameter LLM specialized for code generation.
  </p>

  <div class="image-gallery">
    <div class="gallery-item">
      <img src="../assets/images/deepseekcoder_prompt.png" alt="Example of optimized prompt structure">
      <p class="gallery-caption">Fig 1: Optimized prompt structure with explicit sections for code reasoning</p>
    </div>
    <div class="gallery-item">
      <img src="../assets/images/deepseekcoder_results.png" alt="Performance comparison graph">
      <p class="gallery-caption">Fig 2: Performance metrics before and after prompt optimization</p>
    </div>
  </div>

  <h2>Research Background</h2>
  <p>
    Large Language Models (LLMs) like DeepSeekCoder have demonstrated impressive capabilities in code generation but still struggle with accurate reasoning and test creation, especially for complex programming tasks. Our research aimed to evaluate how structured prompting approaches could overcome these limitations without requiring model retraining.
  </p>
  
  <p>
    We conducted our experiments using DeepSeekCoder-7B-Instruct model, which has 7 billion parameters and was trained on a diverse corpus of code from multiple programming languages with a focus on Python development.
  </p>

  <h2>Technical Challenges & Solutions</h2>
  
  <div class="challenge-solution">
    <div class="challenge">
      <h3>Challenge 1: Semantic Misinterpretation</h3>
      <p>The model frequently misinterpreted task requirements, particularly when problems involved implicit constraints or domain-specific terminology. In 37% of test cases, the model generated syntactically correct code that failed to meet the problem's semantic requirements.</p>
    </div>
    <div class="solution">
      <h3>Solution</h3>
      <p>We restructured prompts to include explicit sections for "Requirements Analysis" and "Edge Cases," forcing the model to reason through problem constraints before generating solutions. This approach reduced semantic misinterpretation by 52% in our benchmark test suite.</p>
    </div>
  </div>
  
  <div class="challenge-solution">
    <div class="challenge">
      <h3>Challenge 2: Inconsistent Test Generation</h3>
      <p>Initial test generation achieved only 43% coverage of critical code paths and often missed edge cases. Tests frequently contained incorrect assertions based on faulty reasoning about expected outputs.</p>
    </div>
    <div class="solution">
      <h3>Solution</h3>
      <p>We developed a unique "test-first" prompt structure that required the model to generate expected test outcomes before implementing the solution code. By reversing this workflow, we achieved a 20% increase in test coverage and significantly improved assertion correctness.</p>
    </div>
  </div>
  
  <div class="challenge-solution">
    <div class="challenge">
      <h3>Challenge 3: Prompt Sensitivity & Consistency</h3>
      <p>Minor variations in prompt wording led to dramatically different output quality. The model was highly sensitive to the order and phrasing of requirements, making results unpredictable.</p>
    </div>
    <div class="solution">
      <h3>Solution</h3>
      <p>Through systematic experimentation with 230+ prompt variations, we identified key structural patterns that improved stability. We developed a "format enforcer" section in our prompts that explicitly directed the model's reasoning process, reducing output variance by 64%.</p>
    </div>
  </div>

  <h2>Prompt Engineering Methodology</h2>
  <p>
    Our research developed a systematic approach to prompt engineering with the following components:
  </p>
  
  <ul>
    <li><strong>Explicit Problem Decomposition:</strong> Breaking down complex problems into smaller, more manageable components</li>
    <li><strong>Step-by-Step Reasoning:</strong> Guiding the model through a sequence of reasoning steps before presenting the final solution</li>
    <li><strong>Enforced Structure:</strong> Requiring specific sections like "Requirements Analysis," "Edge Cases," "Test Cases," and "Implementation"</li>
    <li><strong>Contextual Clues:</strong> Providing domain-specific terminology and constraints that frame the problem appropriately</li>
    <li><strong>Self-Verification:</strong> Adding a final check step where the model validates its own solution against the original requirements</li>
  </ul>
  
  <p>
    We found that the most effective prompts followed this template structure:
  </p>
  
  <pre style="background-color: #f5f5f5; padding: 1rem; border-radius: 4px; overflow-x: auto;">
  # Task Description
  [Clear description of the programming task]
  
  # Requirements Analysis
  [Explicit instruction for the model to analyze the requirements]
  
  # Edge Cases to Consider
  [Instruction to identify potential edge cases]
  
  # Expected Test Cases
  [Instruction to generate test cases before implementation]
  
  # Implementation
  [Instruction to implement the solution]
  
  # Self-Verification
  [Instruction to verify that the solution meets all requirements]
  </pre>

  <h2>Methodology & Implementation</h2>
  <p>
    We created a systematic testing framework to evaluate prompt effectiveness:
  </p>
  <ol>
    <li><strong>Benchmark Development:</strong> Compiled 45 coding problems with varying complexity and domain focus</li>
    <li><strong>Prompt Templating System:</strong> Created a parameterized template engine to generate structured prompts</li>
    <li><strong>Evaluation Pipeline:</strong> Automated testing of generated code against reference solutions</li>
    <li><strong>Metrics Tracking:</strong> Measured syntactic correctness, semantic accuracy, test coverage, and execution time</li>
  </ol>

  <p>
    For implementation, we used Python to develop:
  </p>
  <ul>
    <li>A custom wrapper around the DeepSeekCoder API to standardize interactions</li>
    <li>A prompt template engine with Jinja2 for systematic template generation</li>
    <li>An automated testing harness to execute and validate generated code</li>
    <li>Statistical analysis tools to measure performance improvements</li>
  </ul>

  <h2>Results & Impact</h2>
  
  <div class="metrics-container">
    <div class="metric">
      <div class="metric-value">50%</div>
      <div class="metric-label">Improvement in prediction accuracy</div>
    </div>
    <div class="metric">
      <div class="metric-value">20%</div>
      <div class="metric-label">Increase in test coverage</div>
    </div>
    <div class="metric">
      <div class="metric-value">64%</div>
      <div class="metric-label">Reduction in output variance</div>
    </div>
    <div class="metric">
      <div class="metric-value">3.2x</div>
      <div class="metric-label">Better handling of edge cases</div>
    </div>
  </div>

  <p>
    Our research demonstrated that carefully structured prompts can significantly enhance an LLM's reasoning capabilities for code generation tasks. Key findings include:
  </p>
  
  <ul>
    <li>Explicit reasoning steps in prompts improved logical accuracy without requiring model retraining</li>
    <li>Breaking complex problems into smaller reasoning components yielded better results than end-to-end prompting</li>
    <li>Domain-specific template patterns emerged that could be generalized across different problem types</li>
    <li>The benefits of structured prompting were more pronounced for complex tasks involving multiple constraints or edge cases</li>
  </ul>

  <h2>Specific Examples</h2>
  <p>
    One illustrative example from our research involved a problem requiring the implementation of a function to find the longest substring with at most K distinct characters. With a standard prompt, DeepSeekCoder produced a solution that:
  </p>
  <ul>
    <li>Failed to handle empty string edge cases</li>
    <li>Used inefficient data structures resulting in O(n²) complexity</li>
    <li>Generated incomplete test cases missing critical scenarios</li>
  </ul>
  
  <p>
    After applying our structured prompting technique, the model:
  </p>
  <ul>
    <li>Correctly identified and handled all edge cases including empty strings</li>
    <li>Implemented an optimal sliding window approach with O(n) complexity</li>
    <li>Generated comprehensive test cases covering all boundary conditions</li>
    <li>Added input validation with appropriate error handling</li>
  </ul>

  <h2>Skills Applied</h2>
  <ul>
    <li>Prompt Engineering</li>
    <li>Natural Language Processing</li>
    <li>Python Programming</li>
    <li>Statistical Analysis</li>
    <li>Large Language Model Operation</li>
    <li>Software Testing Methodologies</li>
    <li>Experimental Design</li>
    <li>Technical Documentation</li>
    <li>Teamwork & Collaboration</li>
  </ul>

  <h2>Future Work</h2>
  <p>
    Our research identified several promising directions for future work:
  </p>
  <ul>
    <li>Exploring automated prompt optimization techniques that can evolve effective prompts without manual engineering</li>
    <li>Developing domain-specific prompt templates for different programming paradigms (functional, object-oriented, etc.)</li>
    <li>Investigating the transferability of prompt patterns across different code LLMs</li>
    <li>Creating hybrid approaches that combine prompt engineering with fine-tuning for optimal performance</li>
  </ul>

  <h2>Resources & References</h2>
  <ul>
    <li><strong>GitHub Repository:</strong> <a href="https://github.com/YuxuanMa-sys/CS598JBR-Team-16" target="_blank">DeepSeekCoder Repo</a></li>
    <li><strong>Project Report:</strong> <a href="../assets/deepseekcoder_report.pdf" target="_blank">CS598.JBR Report</a></li>
  </ul>
</div>

