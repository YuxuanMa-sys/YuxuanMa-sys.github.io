---
layout: default
title: "About Me"
---

<!-- Include Font Awesome for icons -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">

<style>
  /* Container for the About page */
  .about-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 2rem;
    font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
    color: #333;
  }

  /* Header styles */
  .about-header {
    text-align: center;
    margin-bottom: 2rem;
  }
  .about-header h1 {
    font-size: 3rem;
    margin-bottom: 0.5rem;
    color: #2c3e50;
  }
  .about-header p {
    font-size: 1.2rem;
    color: #555;
  }

  /* Section titles */
  .section-title {
    border-bottom: 2px solid #ddd;
    padding-bottom: 0.5rem;
    margin-top: 2rem;
    font-size: 1.8rem;
    color: #2c3e50;
  }

  /* Section content */
  .section-content p, .section-content li {
    line-height: 1.6;
    margin: 1rem 0;
  }
  .section-content ul {
    list-style: disc;
    padding-left: 1.5rem;
  }

  /* Contact links styling */
  .contact-links a {
    margin-right: 1rem;
    text-decoration: none;
    color: #007BFF;
    font-weight: bold;
  }
  .contact-links a:hover {
    text-decoration: underline;
  }

  /* Resume link button */
  .resume-link {
    display: inline-block;
    margin-top: 1rem;
    padding: 0.6rem 1.2rem;
    background: #007BFF;
    color: #fff;
    border-radius: 5px;
    text-decoration: none;
    transition: background 0.3s ease;
  }
  .resume-link:hover {
    background: #0056b3;
  }
</style>

<div class="about-container">
  <div class="about-header">
    <h1>Yuxuan (Vincent) Ma</h1>
    <p>Graduate Student in Computer Science & Electrical Engineering | Software Enthusiast</p>
  </div>

  <div class="section-content">
    <h2 class="section-title">Education</h2>
    <p><strong>Master of Computer Science</strong><br>
       University of Illinois Urbana-Champaign<br>
       <em>Aug. 2024 – Dec. 2025</em> — GPA: 4.00/4.00</p>
    <p><strong>B.S. in Electrical Engineering, Minor in Computer Science</strong><br>
       University of Illinois Urbana-Champaign<br>
       <em>Aug. 2021 – May 2024</em> — GPA: 3.65/4.00, Core GPA: 3.857/4.00</p>
  </div>

  <div class="section-content">
    <h2 class="section-title">Experience</h2>
    <p><strong>Software Engineering Intern</strong> at Horus Intelligence Solutions (Urbana, IL)<br>
       <em>Jun. 2022 – Aug. 2022</em></p>
    <ul>
      <li>Optimized data collection and analysis pipelines to deliver actionable insights.</li>
      <li>Redesigned scalable web scraping tools using Python, improving efficiency.</li>
      <li>Enhanced data validation pipelines to reduce inconsistencies and errors.</li>
    </ul>
  </div>

  <div class="section-content">
    <h2 class="section-title">Projects</h2>
    <p>Some highlights of my work include:</p>
    <ul>
      <li><strong><a href="/projects/deepseekcoder.html">DeepSeekCoder</a></strong> – Improved code reasoning and test generation via tailored prompt engineering.</li>
      <li><strong><a href="/projects/steamgenie.html">SteamGenie</a></strong> – An interactive Steam game recommendation app built with React, Express.js, and MongoDB.</li>
      <li><strong><a href="/projects/robotic-task-execution.html">Autonomous Multi-Step Robotic Task Execution System</a></strong> – A robust robotic control system developed in C, MATLAB, and Simulink.</li>
    </ul>
  </div>

  <div class="section-content">
    <h2 class="section-title">Contact</h2>
    <div class="contact-links">
      <a href="mailto:mayuxuan135@gmail.com"><i class="fas fa-envelope"></i> Email</a>
      <a href="https://www.linkedin.com/in/yuxuan-ma-23b7671a5/"><i class="fab fa-linkedin"></i> LinkedIn</a>
      <a href="https://github.com/YuxuanMa-sys"><i class="fab fa-github"></i> GitHub</a>
    </div>
  </div>

  <div class="section-content">
    <h2 class="section-title">Resume</h2>
    <p>For a detailed overview of my background and experience, please download my full resume:</p>
    <a class="resume-link" href="{{ '/Yuxuan (Vincent) Ma-ResumeV2.pdf' | relative_url }}" target="_blank">Download Resume (PDF)</a>
  </div>
</div>
