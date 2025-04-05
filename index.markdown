---
layout: default
title: "Home"
---

<!-- Inline CSS for styling -->
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

  /* Container styling */
  .home-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
    font-family: 'Inter', 'Segoe UI', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    color: var(--text-color);
    line-height: 1.6;
  }

  /* Hero section styling - modern glassmorphism */
  .home-hero {
    text-align: center;
    padding: 8rem 2rem;
    background: linear-gradient(135deg, rgba(67, 97, 238, 0.8), rgba(247, 37, 133, 0.8)), 
                url('/assets/bg.jpg') no-repeat center center/cover;
    color: var(--white);
    border-radius: 16px;
    margin-bottom: 4rem;
    box-shadow: var(--box-shadow);
    position: relative;
    overflow: hidden;
    backdrop-filter: blur(5px);
    animation: fadeIn 1s ease-in-out;
  }

  .home-hero::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: radial-gradient(circle at top right, rgba(247, 37, 133, 0.3), transparent 50%);
    z-index: 0;
  }

  .home-hero h1 {
    font-size: 4rem;
    font-weight: 800;
    margin-bottom: 1rem;
    position: relative;
    z-index: 1;
    text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
  }

  .home-hero p {
    font-size: 1.6rem;
    font-weight: 400;
    max-width: 700px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }

  /* Section title styling */
  .section-title {
    text-align: center;
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 3rem;
    color: var(--text-color);
    position: relative;
    display: inline-block;
    padding-bottom: 0.5rem;
    left: 50%;
    transform: translateX(-50%);
  }
  
  .section-title::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 25%;
    width: 50%;
    height: 4px;
    background: linear-gradient(to right, var(--primary-color), var(--accent-color));
    border-radius: 5px;
  }

  .section-title i {
    margin-right: 0.5rem;
    color: var(--accent-color);
  }

  /* Carousel styling - modernized */
  .carousel-container {
    position: relative;
    max-width: 100%;
    margin: 2rem auto 5rem;
    padding: 1rem;
  }

  .carousel {
    display: flex;
    overflow-x: auto;
    scroll-behavior: smooth;
    padding: 2rem 0.5rem;
    gap: 1.5rem;
    -ms-overflow-style: none;  /* IE and Edge */
    scrollbar-width: none;  /* Firefox */
  }

  .carousel::-webkit-scrollbar {
    display: none; /* Hide scrollbar for Chrome, Safari and Opera */
  }

  .carousel-item {
    width: 280px;
    background: var(--white);
    border-radius: 12px;
    padding: 1.5rem;
    text-align: center;
    flex-shrink: 0;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    text-decoration: none;
    color: inherit;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
    border: 1px solid rgba(0, 0, 0, 0.05);
    position: relative;
    overflow: hidden;
  }

  .carousel-item::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 5px;
    background: linear-gradient(to right, var(--primary-color), var(--accent-color));
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.3s ease;
  }

  .carousel-item:hover {
    transform: translateY(-10px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  }

  .carousel-item:hover::before {
    transform: scaleX(1);
  }

  .carousel-item i {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    color: var(--primary-color);
    background: rgba(67, 97, 238, 0.1);
    width: 80px;
    height: 80px;
    line-height: 80px;
    border-radius: 50%;
    display: inline-block;
    transition: all 0.3s ease;
  }

  .carousel-item:hover i {
    transform: scale(1.1);
    color: var(--accent-color);
    background: rgba(247, 37, 133, 0.1);
  }

  .carousel-item h3 {
    font-size: 1.3rem;
    margin: 1rem 0;
    color: var(--text-color);
    font-weight: 600;
  }

  .carousel-item p {
    font-size: 0.95rem;
    color: var(--text-light);
    word-wrap: break-word;
    line-height: 1.5;
    height: 4.5em;
    overflow: hidden;
  }

  .carousel-btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: var(--white);
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    z-index: 2;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--primary-color);
    transition: all 0.3s ease;
  }

  .carousel-btn:hover {
    background: var(--primary-color);
    color: var(--white);
    box-shadow: 0 6px 20px rgba(67, 97, 238, 0.3);
  }

  .carousel-btn.left {
    left: 10px;
  }

  .carousel-btn.right {
    right: 10px;
  }

  /* Skills section styling - glassmorphism effect */
  .skills-section {
    background: linear-gradient(135deg, var(--bg-dark), #3a3d5a);
    padding: 4rem 3rem;
    border-radius: 16px;
    color: var(--white);
    margin: 5rem 0;
    text-align: center;
    box-shadow: var(--box-shadow);
    position: relative;
    overflow: hidden;
  }

  .skills-section::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: radial-gradient(circle at bottom left, rgba(76, 201, 240, 0.2), transparent 50%);
    z-index: 0;
  }

  .skills-section h2 {
    font-size: 2.5rem;
    margin-bottom: 3rem;
    color: var(--white);
    font-weight: 700;
    position: relative;
    z-index: 1;
  }

  .skills-section h2 i {
    margin-right: 0.5rem;
    color: var(--success-color);
  }

  .skills-container {
    display: flex;
    justify-content: space-around;
    align-items: flex-start;
    flex-wrap: wrap;
    margin-top: 2rem;
    position: relative;
    z-index: 1;
  }

  .skill-column {
    width: 48%;
    margin-bottom: 2rem;
    min-width: 280px;
  }

  .skill-bar {
    margin-bottom: 2rem;
    position: relative;
  }

  .skill-label {
    display: flex;
    justify-content: space-between;
    margin-bottom: 0.8rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-size: 0.85rem;
  }

  .bar {
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 8px;
    overflow: hidden;
    position: relative;
    height: 10px;
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.2);
  }

  .progress {
    background: linear-gradient(to right, var(--primary-light), var(--accent-color));
    height: 100%;
    position: relative;
    border-radius: 8px;
    transition: width 1.5s cubic-bezier(0.1, 0.5, 0.1, 1);
    width: 0;
  }

  /* Other skills chips */
  .other-skills {
    margin-top: 3rem;
    position: relative;
    z-index: 1;
  }

  .other-skills h3 {
    font-size: 1.5rem;
    margin-bottom: 1.5rem;
    font-weight: 600;
    color: var(--white);
  }

  .skill-chip {
    display: inline-block;
    background-color: rgba(255, 255, 255, 0.1);
    color: var(--white);
    padding: 0.6rem 1.2rem;
    border-radius: 99px;
    margin: 0.5rem;
    font-size: 0.9rem;
    transition: all 0.3s ease;
    backdrop-filter: blur(5px);
    border: 1px solid rgba(255, 255, 255, 0.1);
  }

  .skill-chip:hover {
    background-color: var(--primary-color);
    transform: translateY(-3px);
    box-shadow: 0 4px 15px rgba(67, 97, 238, 0.3);
  }

  /* Contact section styling */
  .contact-section {
    text-align: center;
    margin-top: 3rem;
    padding: 3rem;
    border-radius: 16px;
    background-color: var(--bg-light);
    box-shadow: var(--box-shadow);
  }

  .contact-section a {
    display: inline-block;
    color: var(--white);
    text-decoration: none;
    font-weight: 600;
    padding: 0.8rem 2rem;
    background: linear-gradient(to right, var(--primary-color), var(--accent-color));
    border-radius: 30px;
    margin-top: 1rem;
    transition: all 0.3s ease;
    box-shadow: 0 4px 15px rgba(67, 97, 238, 0.3);
  }

  .contact-section a:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(67, 97, 238, 0.4);
  }

  /* Animations */
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* Responsive design */
  @media screen and (max-width: 768px) {
    .home-hero {
      padding: 6rem 1rem;
    }
    
    .home-hero h1 {
      font-size: 3rem;
    }
    
    .home-hero p {
      font-size: 1.3rem;
    }
    
    .skills-section {
      padding: 3rem 1.5rem;
    }
    
    .skill-column {
      width: 100%;
    }
    
    .carousel-btn {
      width: 40px;
      height: 40px;
      font-size: 1.2rem;
    }
  }

  @media screen and (max-width: 480px) {
    .home-hero h1 {
      font-size: 2.5rem;
    }
    
    .section-title {
      font-size: 2rem;
    }
    
    .carousel-item {
      width: 240px;
    }
  }

  /* About Me Section Styling */
  .about-section {
    margin: 5rem 0;
    animation: fadeIn 1s ease-in-out;
  }
  
  .about-content {
    display: flex;
    align-items: center;
    gap: 3rem;
    margin-top: 2rem;
    background: var(--white);
    border-radius: 16px;
    padding: 3rem;
    box-shadow: var(--box-shadow);
  }
  
  .about-image {
    flex: 0 0 300px;
  }
  
  .image-container {
    width: 300px;
    height: 300px;
    border-radius: 50%;
    overflow: hidden;
    border: 5px solid transparent;
    background-image: linear-gradient(white, white), 
                      linear-gradient(to right, var(--primary-color), var(--accent-color));
    background-origin: border-box;
    background-clip: padding-box, border-box;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  }
  
  .about-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s ease;
  }
  
  .image-container:hover img {
    transform: scale(1.05);
  }
  
  .about-text {
    flex: 1;
  }
  
  .about-text p {
    margin-bottom: 1.5rem;
    font-size: 1.1rem;
    line-height: 1.8;
    color: var(--text-color);
  }
  
  .read-more-btn {
    display: inline-block;
    color: var(--primary-color);
    text-decoration: none;
    font-weight: 600;
    transition: all 0.3s ease;
  }
  
  .read-more-btn i {
    margin-left: 0.5rem;
    transition: transform 0.3s ease;
  }
  
  .read-more-btn:hover {
    color: var(--accent-color);
  }
  
  .read-more-btn:hover i {
    transform: translateX(5px);
  }

  /* Education Timeline Styling */
  .education-section {
    margin: 5rem 0;
    animation: fadeIn 1s ease-in-out;
  }
  
  .timeline {
    position: relative;
    max-width: 1000px;
    margin: 3rem auto 0;
    padding: 2rem 0;
  }
  
  .timeline::before {
    content: '';
    position: absolute;
    width: 4px;
    background: linear-gradient(to bottom, var(--primary-color), var(--accent-color));
    top: 0;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    border-radius: 4px;
  }
  
  .timeline-item {
    position: relative;
    width: 50%;
    padding: 0 3rem 2rem 0;
    text-align: right;
    animation: slideRight 0.6s ease-in-out;
  }
  
  .timeline-item:nth-child(even) {
    left: 50%;
    padding: 0 0 2rem 3rem;
    text-align: left;
    animation: slideLeft 0.6s ease-in-out;
  }
  
  .timeline-dot {
    position: absolute;
    width: 24px;
    height: 24px;
    background: linear-gradient(to right, var(--primary-color), var(--accent-color));
    border-radius: 50%;
    top: 0;
    right: -12px;
    z-index: 1;
    box-shadow: 0 0 0 4px rgba(67, 97, 238, 0.2);
  }
  
  .timeline-item:nth-child(even) .timeline-dot {
    left: -12px;
    right: auto;
  }
  
  .timeline-date {
    display: inline-block;
    padding: 0.5rem 1rem;
    background: var(--accent-color);
    color: var(--white);
    border-radius: 30px;
    font-weight: 600;
    font-size: 0.9rem;
    margin-bottom: 0.5rem;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  }
  
  .timeline-content {
    background: var(--white);
    padding: 1.5rem;
    border-radius: 12px;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
    transition: all 0.3s ease;
  }
  
  .timeline-content:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.12);
  }
  
  .timeline-content h3 {
    color: var(--primary-color);
    margin-bottom: 0.5rem;
    font-weight: 600;
  }
  
  .timeline-content p {
    color: var(--text-color);
    margin-bottom: 0.5rem;
  }
  
  .timeline-content p:last-child {
    margin-bottom: 0;
  }
  
  @keyframes slideRight {
    from { opacity: 0; transform: translateX(-50px); }
    to { opacity: 1; transform: translateX(0); }
  }
  
  @keyframes slideLeft {
    from { opacity: 0; transform: translateX(50px); }
    to { opacity: 1; transform: translateX(0); }
  }

  /* Testimonials Styling */
  .testimonials-section {
    margin: 5rem 0;
    animation: fadeIn 1s ease-in-out;
  }
  
  .testimonials-container {
    display: flex;
    gap: 2rem;
    margin-top: 3rem;
    flex-wrap: wrap;
    justify-content: center;
  }
  
  .testimonial {
    flex: 1;
    min-width: 300px;
    max-width: 500px;
    background: var(--white);
    padding: 2rem;
    border-radius: 12px;
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
    position: relative;
    transition: all 0.3s ease;
  }
  
  .testimonial:hover {
    transform: translateY(-10px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  }
  
  .testimonial::before {
    content: '';
    position: absolute;
    width: 100%;
    height: 5px;
    background: linear-gradient(to right, var(--primary-color), var(--accent-color));
    top: 0;
    left: 0;
    border-radius: 12px 12px 0 0;
  }
  
  .quote {
    font-size: 2.5rem;
    color: var(--accent-color);
    opacity: 0.2;
    position: absolute;
    top: 1rem;
    left: 1rem;
  }
  
  .testimonial p {
    position: relative;
    z-index: 1;
    font-size: 1.1rem;
    line-height: 1.8;
    margin-bottom: 1.5rem;
    color: var(--text-color);
    font-style: italic;
  }
  
  .testimonial-author {
    text-align: right;
    border-top: 1px solid rgba(0, 0, 0, 0.05);
    padding-top: 1rem;
  }
  
  .author-name {
    font-weight: 700;
    color: var(--primary-color);
    margin-bottom: 0.2rem;
  }
  
  .author-title {
    font-size: 0.9rem;
    color: var(--text-light);
  }

  /* Responsive adjustments for new sections */
  @media screen and (max-width: 992px) {
    .timeline::before {
      left: 30px;
    }
    
    .timeline-item {
      width: 100%;
      padding-right: 0;
      padding-left: 6rem;
      text-align: left;
    }
    
    .timeline-item:nth-child(even) {
      left: 0;
      padding-left: 6rem;
    }
    
    .timeline-dot {
      left: 28px;
      right: auto;
    }
    
    .timeline-item:nth-child(even) .timeline-dot {
      left: 28px;
    }
  }
  
  @media screen and (max-width: 768px) {
    .about-content {
      flex-direction: column;
      padding: 2rem;
    }
    
    .about-image {
      flex: none;
      margin-bottom: 2rem;
    }
    
    .timeline-item {
      padding-left: 5rem;
    }
    
    .timeline-item:nth-child(even) {
      padding-left: 5rem;
    }
    
    .testimonials-container {
      flex-direction: column;
      align-items: center;
    }
    
    .testimonial {
      max-width: 100%;
    }
  }
  
  @media screen and (max-width: 480px) {
    .timeline-item {
      padding-left: 4rem;
    }
    
    .timeline-item:nth-child(even) {
      padding-left: 4rem;
    }
    
    .timeline::before {
      left: 20px;
    }
    
    .timeline-dot {
      left: 18px;
    }
    
    .timeline-item:nth-child(even) .timeline-dot {
      left: 18px;
    }
  }
</style>

<!-- HTML Content -->
<div class="home-container">
  <div class="home-hero">
    <h1>Welcome to My Portfolio</h1>
    <p>Discover my favorite projects, learn more about me, and get in touch!</p>
  </div>

  <!-- Projects Section Title -->
  <h2 class="section-title"><i class="fas fa-toolbox"></i> Projects</h2>

  <!-- Carousel Section -->
  <div class="carousel-container">
    <button class="carousel-btn left" id="prevBtn"><i class="fas fa-chevron-left"></i></button>
    <div class="carousel" id="projectsCarousel">
      <a href="/projects/deepseekcoder.html" class="carousel-item">
        <i class="fas fa-code"></i>
        <h3>Enhancing Code Reasoning and Test Generation</h3>
        <p>Improved code reasoning &amp; test generation via tailored prompt engineering.</p>
      </a>
      <a href="/projects/reproducibility.html" class="carousel-item">
        <i class="fas fa-vial"></i>
        <h3>Reproducibility Research for Research Software</h3>
        <p>Docker-based solutions for replicating research artifacts &amp; standardizing environments.</p>
      </a>
      <a href="/projects/steamgenie.html" class="carousel-item">
        <i class="fas fa-gamepad"></i>
        <h3>SteamGenie</h3>
        <p>A React/Express app providing personalized Steam game recommendations.</p>
      </a>
      <a href="/projects/robotic-task-execution.html" class="carousel-item">
        <i class="fas fa-robot"></i>
        <h3>Autonomous Multi-Step Robotic Task Execution</h3>
        <p>A control system for a CRS robot arm, enabling precise navigation &amp; obstacle avoidance.</p>
      </a>
      <a href="/projects/habit-forming-keystation.html" class="carousel-item">
        <i class="fas fa-keyboard"></i>
        <h3>Habit-Forming KeyStation</h3>
        <p>A device leveraging sensor fusion &amp; RF tracking to help users consistently find their keys.</p>
      </a>
      <a href="/projects/fpga-flappy-bird.html" class="carousel-item">
        <i class="fas fa-bolt"></i>
        <h3>Dynamic "Flappy Bird" on FPGA</h3>
        <p>Hardware-level logic for real-time rendering &amp; interaction, implementing Flappy Bird on an FPGA.</p>
      </a>
      <a href="/projects/ros-robotics-programming.html" class="carousel-item">
        <i class="fas fa-cogs"></i>
        <h3>ROS Robotics Programming</h3>
        <p>Robotic manipulation &amp; navigation in a 6-DOF environment using ROS.</p>
      </a>
      <a href="/projects/reaction-wheel-pendulum.html" class="carousel-item">
        <i class="fas fa-balance-scale"></i>
        <h3>Reaction Wheel Pendulum</h3>
        <p>Stabilize a pendulum at its inverted position using reaction wheel dynamics &amp; feedback loops.</p>
      </a>
      <a href="/projects/video-game-sales-analysis.html" class="carousel-item">
        <i class="fas fa-chart-line"></i>
        <h3>Regional Video Games Sales Analysis</h3>
        <p>Statistical modeling to uncover trends in global video game sales across regions.</p>
      </a>
      <a href="/projects/cryptography-toolkit.html" class="carousel-item">
        <i class="fas fa-lock"></i>
        <h3>CryptoToolkit</h3>
        <p>Comprehensive implementation of cryptographic primitives including encryption, digital signatures, and blockchain fundamentals.</p>
      </a>
    </div>
    <button class="carousel-btn right" id="nextBtn"><i class="fas fa-chevron-right"></i></button>
  </div>

  <!-- Skills Section -->
  <section class="skills-section">
    <h2><i class="fas fa-wrench"></i> My Skills</h2>
    <div class="skills-container">
      <!-- Left column -->
      <div class="skill-column">
        <!-- C/C++ -->
        <div class="skill-bar">
          <div class="skill-label">
            <span>C/C++</span>
            <span>70%</span>
          </div>
          <div class="bar">
            <div class="progress" style="width: 0%;" data-width="70%"></div>
          </div>
        </div>

        <!-- Python -->
        <div class="skill-bar">
          <div class="skill-label">
            <span>Python</span>
            <span>80%</span>
          </div>
          <div class="bar">
            <div class="progress" style="width: 0%;" data-width="80%"></div>
          </div>
        </div>

        <!-- Data Structures & Algorithms -->
        <div class="skill-bar">
          <div class="skill-label">
            <span>Data Structure &amp; Algorithms</span>
            <span>70%</span>
          </div>
          <div class="bar">
            <div class="progress" style="width: 0%;" data-width="70%"></div>
          </div>
        </div>
      </div>

      <!-- Right column -->
      <div class="skill-column">
        <!-- JavaScript/TypeScript -->
        <div class="skill-bar">
          <div class="skill-label">
            <span>JavaScript/TypeScript</span>
            <span>50%</span>
          </div>
          <div class="bar">
            <div class="progress" style="width: 0%;" data-width="50%"></div>
          </div>
        </div>

        <!-- Matlab -->
        <div class="skill-bar">
          <div class="skill-label">
            <span>Matlab</span>
            <span>50%</span>
          </div>
          <div class="bar">
            <div class="progress" style="width: 0%;" data-width="50%"></div>
          </div>
        </div>
      </div>
    </div>

    <!-- Other Skills -->
    <div class="other-skills">
      <h3>Other Skills</h3>
      <span class="skill-chip">Machine Learning</span>
      <span class="skill-chip">Embedded Systems</span>
      <span class="skill-chip">Docker</span>
      <span class="skill-chip">AWS</span>
      <span class="skill-chip">Git</span>
      <span class="skill-chip">Data Analysis</span>
      <span class="skill-chip">Parallel Programming</span>
    </div>
  </section>

  <!-- About Me Section -->
  <div class="about-section">
    <h2 class="section-title"><i class="fas fa-user"></i> About Me</h2>
    <div class="about-content">
      <div class="about-image">
        <div class="image-container">
          <img src="{{ '/assets/profile.jpg' | relative_url }}" alt="Yuxuan Ma" onerror="this.src='https://via.placeholder.com/300?text=Profile+Photo'">
        </div>
      </div>
      <div class="about-text">
        <p>Hello! I'm a graduate student in Computer Science with a background in Electrical Engineering at the University of Illinois Urbana-Champaign. My passion lies at the intersection of software engineering, robotics, and AI.</p>
        <p>With experience in full-stack development, embedded systems, and AI applications, I enjoy building solutions that bridge the gap between hardware and software. My academic journey has equipped me with strong analytical skills and a methodical approach to problem-solving.</p>
        <a href="/about/" class="read-more-btn">Read More <i class="fas fa-arrow-right"></i></a>
      </div>
    </div>
  </div>

  <!-- Education Timeline Section -->
  <div class="education-section">
    <h2 class="section-title"><i class="fas fa-graduation-cap"></i> Education</h2>
    <div class="timeline">
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-date">2024 - 2025</div>
        <div class="timeline-content">
          <h3>Master of Computer Science</h3>
          <p>University of Illinois Urbana-Champaign</p>
          <p><i class="fas fa-award"></i> GPA: 4.00/4.00</p>
        </div>
      </div>
      <div class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-date">2021 - 2024</div>
        <div class="timeline-content">
          <h3>B.S. in Electrical Engineering, Minor in Computer Science</h3>
          <p>University of Illinois Urbana-Champaign</p>
          <p><i class="fas fa-award"></i> GPA: 3.65/4.00, Core GPA: 3.857/4.00</p>
        </div>
      </div>
    </div>
  </div>

  <!-- Testimonials Section -->
  <div class="testimonials-section">
    <h2 class="section-title"><i class="fas fa-comment-dots"></i> Testimonials</h2>
    <div class="testimonials-container">
      <div class="testimonial">
        <div class="quote"><i class="fas fa-quote-left"></i></div>
        <p>Yuxuan demonstrated exceptional technical skills and problem-solving abilities during his internship. His contributions to our data pipeline significantly improved our operational efficiency.</p>
        <div class="testimonial-author">
          <p class="author-name">- Jane Smith</p>
          <p class="author-title">Senior Engineer at Horus Intelligence Solutions</p>
        </div>
      </div>
      
      <div class="testimonial">
        <div class="quote"><i class="fas fa-quote-left"></i></div>
        <p>I was impressed by Yuxuan's dedication and technical prowess. His approach to complex problems is methodical and innovative, making him a valuable team member on any project.</p>
        <div class="testimonial-author">
          <p class="author-name">- Dr. John Doe</p>
          <p class="author-title">Assistant Professor, UIUC</p>
        </div>
      </div>
    </div>
  </div>

  <!-- Contact Section -->
  <div class="contact-section">
    <p>Interested in collaborating or have questions?</p>
    <a href="/about/" class="contact-btn">Get in Touch</a>
  </div>
</div>

<!-- Include Font Awesome CDN for icons -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/js/all.min.js"></script>

<!-- JavaScript for carousel and animations -->
<script>
  document.addEventListener('DOMContentLoaded', function() {
    // Carousel functionality
    const carousel = document.getElementById('projectsCarousel');
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    
    // Adjust the scroll amount for one card width plus gap
    const scrollAmount = 300;
    
    prevBtn.addEventListener('click', () => {
      // If at the very left, wrap around to the rightmost position
      if (carousel.scrollLeft === 0) {
        carousel.scrollTo({
          left: carousel.scrollWidth - carousel.clientWidth,
          behavior: 'smooth'
        });
      } else {
        carousel.scrollBy({
          left: -scrollAmount,
          behavior: 'smooth'
        });
      }
    });
    
    nextBtn.addEventListener('click', () => {
      // If at the very right, wrap around to the leftmost position
      if (carousel.scrollLeft + carousel.clientWidth >= carousel.scrollWidth) {
        carousel.scrollTo({
          left: 0,
          behavior: 'smooth'
        });
      } else {
        carousel.scrollBy({
          left: scrollAmount,
          behavior: 'smooth'
        });
      }
    });
    
    // Animate skill bars when they come into view
    const progressBars = document.querySelectorAll('.progress');
    
    // Check if element is in viewport
    function isInViewport(element) {
      const rect = element.getBoundingClientRect();
      return (
        rect.top >= 0 &&
        rect.left >= 0 &&
        rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &&
        rect.right <= (window.innerWidth || document.documentElement.clientWidth)
      );
    }
    
    // Function to animate progress bars
    function animateProgressBars() {
      progressBars.forEach(bar => {
        if (isInViewport(bar) && bar.style.width === '0%') {
          setTimeout(() => {
            bar.style.width = bar.getAttribute('data-width');
          }, 200);
        }
      });
    }
    
    // Animate on load and scroll
    animateProgressBars();
    window.addEventListener('scroll', animateProgressBars);

    // Function to check if an element is in viewport
    function isInViewport(element) {
      const rect = element.getBoundingClientRect();
      return (
        rect.top >= 0 &&
        rect.left >= 0 &&
        rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &&
        rect.right <= (window.innerWidth || document.documentElement.clientWidth)
      );
    }
    
    // Animate timeline items when they come into view
    const timelineItems = document.querySelectorAll('.timeline-item');
    
    function animateTimelineItems() {
      timelineItems.forEach(item => {
        if (isInViewport(item) && !item.classList.contains('animated')) {
          item.classList.add('animated');
          item.style.opacity = '1';
        }
      });
    }
    
    // Set initial state
    timelineItems.forEach(item => {
      item.style.opacity = '0';
    });
    
    // Animate on load and scroll
    animateTimelineItems();
    window.addEventListener('scroll', animateTimelineItems);
  });
</script>
