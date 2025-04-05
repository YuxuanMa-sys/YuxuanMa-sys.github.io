---
layout: default
title: "About Me"
---

<!-- Include Font Awesome and Google Fonts -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">

<style>
  :root {
    --primary-color: #4361ee;
    --primary-light: #4895ef;
    --secondary-color: #3f37c9;
    --accent-color: #f72585;
    --text-color: #2b2d42;
    --text-light: #8d99ae;
    --bg-light: #f8f9fa;
    --bg-dark: #212529;
    --success-color: #4cc9f0;
    --white: #ffffff;
    --box-shadow: 0 10px 30px -15px rgba(0, 0, 0, 0.15);
  }

  /* Base styles */
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  /* Container for the About page */
  .about-container {
    max-width: 900px;
    margin: 2rem auto;
    padding: 2rem;
    font-family: 'Inter', 'Segoe UI', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    color: var(--text-color);
    line-height: 1.6;
    animation: fadeIn 0.8s ease-in-out;
  }

  /* Header styles with glassmorphism */
  .about-header {
    text-align: center;
    margin-bottom: 3rem;
    padding: 3rem;
    background: linear-gradient(135deg, rgba(67, 97, 238, 0.8), rgba(247, 37, 133, 0.8));
    border-radius: 16px;
    color: var(--white);
    position: relative;
    overflow: hidden;
    box-shadow: var(--box-shadow);
  }
  
  .about-header::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: radial-gradient(circle at top right, rgba(247, 37, 133, 0.3), transparent 50%);
    z-index: 0;
  }
  
  .about-header h1 {
    font-size: 3.5rem;
    font-weight: 800;
    margin-bottom: 1rem;
    position: relative;
    z-index: 1;
    text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
  }
  
  .about-header p {
    font-size: 1.3rem;
    color: var(--white);
    max-width: 600px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
    font-weight: 400;
  }

  /* Section container with card-like appearance */
  .section-container {
    background: var(--white);
    border-radius: 12px;
    padding: 2rem;
    margin-bottom: 2rem;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
    transform: translateY(0);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    border-top: 5px solid transparent;
    background-image: linear-gradient(var(--white), var(--white)), 
                      linear-gradient(to right, var(--primary-color), var(--accent-color));
    background-origin: border-box;
    background-clip: padding-box, border-box;
  }

  .section-container:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.1);
  }

  /* Section titles */
  .section-title {
    font-size: 1.8rem;
    color: var(--text-color);
    font-weight: 700;
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
  }

  .section-title i {
    color: var(--accent-color);
    margin-right: 0.8rem;
    font-size: 1.6rem;
  }

  /* Section content */
  .section-content p, .section-content li {
    line-height: 1.8;
    margin: 1rem 0;
    color: var(--text-color);
  }
  
  .section-content strong {
    color: var(--primary-color);
    font-weight: 600;
  }
  
  .section-content em {
    color: var(--text-light);
    font-style: italic;
  }
  
  .section-content ul {
    list-style: none;
    padding-left: 0.5rem;
  }
  
  .section-content li {
    position: relative;
    padding-left: 1.5rem;
    margin-bottom: 0.8rem;
  }
  
  .section-content li::before {
    content: "▹";
    position: absolute;
    left: 0;
    color: var(--accent-color);
    font-size: 1.2rem;
  }
  
  .section-content a {
    color: var(--primary-color);
    text-decoration: none;
    font-weight: 600;
    position: relative;
    transition: all 0.3s ease;
  }
  
  .section-content a::after {
    content: '';
    position: absolute;
    width: 100%;
    height: 2px;
    bottom: -2px;
    left: 0;
    background: linear-gradient(to right, var(--primary-color), var(--accent-color));
    transform: scaleX(0);
    transform-origin: bottom right;
    transition: transform 0.3s ease;
  }
  
  .section-content a:hover::after {
    transform: scaleX(1);
    transform-origin: bottom left;
  }

  /* Contact links styling */
  .contact-links {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    margin-top: 1.5rem;
  }
  
  .contact-links a {
    display: flex;
    align-items: center;
    background-color: var(--bg-light);
    color: var(--primary-color);
    padding: 0.8rem 1.5rem;
    border-radius: 50px;
    text-decoration: none;
    font-weight: 600;
    transition: all 0.3s ease;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
  }
  
  .contact-links a i {
    margin-right: 0.5rem;
    font-size: 1.2rem;
  }
  
  .contact-links a:hover {
    transform: translateY(-3px);
    background-color: var(--primary-color);
    color: var(--white);
    box-shadow: 0 6px 15px rgba(67, 97, 238, 0.3);
  }

  /* CV link button */
  .cv-link {
    display: inline-block;
    margin-top: 1.5rem;
    padding: 1rem 2rem;
    background: linear-gradient(to right, var(--primary-color), var(--accent-color));
    color: var(--white);
    border-radius: 50px;
    text-decoration: none;
    font-weight: 600;
    transition: all 0.3s ease;
    box-shadow: 0 4px 15px rgba(67, 97, 238, 0.3);
  }
  
  .cv-link:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(67, 97, 238, 0.4);
  }
  
  .cv-link i {
    margin-right: 0.5rem;
  }
  
  /* Animations */
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  
  /* Education card specific styling */
  .education-item {
    margin-bottom: 1.5rem;
    padding-bottom: 1.5rem;
    border-bottom: 1px solid rgba(0, 0, 0, 0.05);
  }
  
  .education-item:last-child {
    border-bottom: none;
    margin-bottom: 0;
    padding-bottom: 0;
  }
  
  /* Responsive design */
  @media screen and (max-width: 768px) {
    .about-header {
      padding: 2rem 1rem;
    }
    
    .about-header h1 {
      font-size: 2.5rem;
    }
    
    .about-header p {
      font-size: 1.1rem;
    }
    
    .section-container {
      padding: 1.5rem;
    }
    
    .contact-links {
      flex-direction: column;
      gap: 0.8rem;
    }
    
    .contact-links a {
      width: 100%;
      justify-content: center;
    }
  }
</style>

<div class="about-container">
  <div class="about-header">
    <h1>Yuxuan (Vincent) Ma</h1>
    <p>Graduate Student in Computer Science & Electrical Engineering | Software Enthusiast</p>
  </div>

  <div class="section-container">
    <h2 class="section-title"><i class="fas fa-graduation-cap"></i>Education</h2>
    <div class="section-content">
      <div class="education-item">
        <p><strong>Master of Computer Science</strong><br>
           University of Illinois Urbana-Champaign<br>
           <em>Aug. 2024 – Dec. 2025</em> — GPA: 4.00/4.00</p>
      </div>
      <div class="education-item">
        <p><strong>B.S. in Electrical Engineering, Minor in Computer Science</strong><br>
           University of Illinois Urbana-Champaign<br>
           <em>Aug. 2021 – May 2024</em> — GPA: 3.65/4.00, Core GPA: 3.857/4.00</p>
      </div>
    </div>
  </div>

  <div class="section-container">
    <h2 class="section-title"><i class="fas fa-briefcase"></i>Experience</h2>
    <div class="section-content">
      <p><strong>Software Engineering Intern</strong> at Horus Intelligence Solutions (Urbana, IL)<br>
         <em>Jun. 2022 – Aug. 2022</em></p>
      <ul>
        <li>Optimized data collection and analysis pipelines to deliver actionable insights.</li>
        <li>Redesigned scalable web scraping tools using Python, improving efficiency.</li>
        <li>Enhanced data validation pipelines to reduce inconsistencies and errors.</li>
      </ul>
    </div>
  </div>

  <div class="section-container">
    <h2 class="section-title"><i class="fas fa-code-branch"></i>Projects</h2>
    <div class="section-content">
      <p>Some highlights of my work include:</p>
      <ul>
        <li><strong><a href="/projects/deepseekcoder.html">DeepSeekCoder</a></strong> – Improved code reasoning and test generation via tailored prompt engineering.</li>
        <li><strong><a href="/projects/steamgenie.html">SteamGenie</a></strong> – An interactive Steam game recommendation app built with React, Express.js, and MongoDB.</li>
        <li><strong><a href="/projects/robotic-task-execution.html">Autonomous Multi-Step Robotic Task Execution System</a></strong> – A robust robotic control system developed in C, MATLAB, and Simulink.</li>
      </ul>
    </div>
  </div>

  <div class="section-container">
    <h2 class="section-title"><i class="fas fa-envelope-open-text"></i>Contact</h2>
    <div class="section-content">
      <p>Feel free to reach out to me through any of the following channels:</p>
      <div class="contact-links">
        <a href="mailto:mayuxuan135@gmail.com"><i class="fas fa-envelope"></i> Email</a>
        <a href="https://www.linkedin.com/in/yuxuan-ma-23b7671a5/"><i class="fab fa-linkedin"></i> LinkedIn</a>
        <a href="https://github.com/YuxuanMa-sys"><i class="fab fa-github"></i> GitHub</a>
      </div>
    </div>
  </div>

  <div class="section-container">
    <h2 class="section-title"><i class="fas fa-file-alt"></i>Curriculum Vitae</h2>
    <div class="section-content">
      <p>For a detailed overview of my background and experience, please download my full CV:</p>
      <a class="cv-link" href="{{ '/assets/CV.pdf' | relative_url }}" target="_blank"><i class="fas fa-download"></i> Download CV (PDF)</a>
    </div>
  </div>
</div>
