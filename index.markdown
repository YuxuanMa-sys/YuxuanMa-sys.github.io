---
layout: default
title: "Home"
---

<!-- Inline CSS for styling -->
<style>
  /* Container styling */
  .home-container {
    max-width: 900px;
    margin: 0 auto;
    padding: 2rem;
    font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
    color: #333;
  }

  /* Hero section styling */
  .home-hero {
    text-align: center;
    padding: 3rem 0;
    background: url('/assets/bg.jpg') no-repeat center center/cover;
    color: #fff;
    border-radius: 8px;
  }
  .home-hero h1 {
    font-size: 3.5rem;
    margin-bottom: 0.5rem;
  }
  .home-hero p {
    font-size: 1.5rem;
    margin: 0;
  }

  /* Carousel styling */
  .carousel-container {
    position: relative;
    max-width: 900px;
    margin: 2rem auto;
    overflow: hidden;
  }
  .carousel {
    display: flex;
    overflow-x: auto;
    scroll-behavior: smooth;
    padding: 1rem;
    gap: 1rem;
  }
  .carousel-item {
    width: 250px;  /* Fixed width for each card */
    background: #fff;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 1rem;
    text-align: center;
    flex-shrink: 0;
    transition: transform 0.2s ease, background-color 0.2s ease;
    text-decoration: none;
    color: inherit;
  }
  .carousel-item:hover {
    transform: translateY(-5px);
    background-color: #f9f9f9;
  }
  .carousel-item i {
    font-size: 2rem;
    margin-bottom: 0.5rem;
    color: #2c3e50;
  }
  .carousel-item h3 {
    font-size: 1.2rem;
    margin: 0.5rem 0;
    color: #2c3e50;
  }
  .carousel-item p {
    font-size: 0.9rem;
    color: #555;
    word-wrap: break-word;
  }
  .carousel-btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(255,255,255,0.8);
    border: none;
    font-size: 2rem;
    cursor: pointer;
    padding: 0.5rem;
    border-radius: 50%;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    z-index: 2;
  }
  .carousel-btn.left {
    left: 10px;
  }
  .carousel-btn.right {
    right: 10px;
  }

  /* Contact section styling */
  .contact-section {
    text-align: center;
    margin-top: 3rem;
    padding-top: 2rem;
    border-top: 1px solid #ddd;
  }
  .contact-section a {
    color: #007BFF;
    text-decoration: none;
    font-weight: bold;
  }
  .contact-section a:hover {
    text-decoration: underline;
  }
</style>

<!-- HTML Content -->
<div class="home-container">
  <div class="home-hero">
    <h1>Welcome to My Portfolio</h1>
    <p>Discover my favorite projects, learn more about me, and get in touch!</p>
  </div>

  <!-- Carousel Section -->
  <div class="carousel-container">
    <button class="carousel-btn left" id="prevBtn">&#10094;</button>
    <div class="carousel" id="projectsCarousel">
      <a href="/projects/deepseekcoder.html" class="carousel-item">
        <i class="fas fa-code"></i>
        <h3>Enhancing Code Reasoning and Test Generation</h3>
        <p>Improved code reasoning & test generation via tailored prompt engineering.</p>
      </a>
      <a href="/projects/reproducibility.html" class="carousel-item">
        <i class="fas fa-vial"></i>
        <h3>Reproducibility Research for Research Software</h3>
        <p>Docker-based solutions for replicating research artifacts & standardizing environments.</p>
      </a>
      <a href="/projects/steamgenie.html" class="carousel-item">
        <i class="fas fa-gamepad"></i>
        <h3>SteamGenie</h3>
        <p>A React/Express app providing personalized Steam game recommendations.</p>
      </a>
      <a href="/projects/robotic-task-execution.html" class="carousel-item">
        <i class="fas fa-robot"></i>
        <h3>Autonomous Multi-Step Robotic Task Execution</h3>
        <p>A control system for a CRS robot arm, enabling precise navigation & obstacle avoidance.</p>
      </a>
      <a href="/projects/habit-forming-keystation.html" class="carousel-item">
        <i class="fas fa-keyboard"></i>
        <h3>Habit-Forming KeyStation</h3>
        <p>A device leveraging sensor fusion & RF tracking to help users consistently find their keys.</p>
      </a>
      <a href="/projects/fpga-flappy-bird.html" class="carousel-item">
        <i class="fas fa-bolt"></i>
        <h3>Dynamic "Flappy Bird" on FPGA</h3>
        <p>Hardware-level logic for real-time rendering & interaction, implementing Flappy Bird on an FPGA.</p>
      </a>
      <a href="/projects/ros-robotics-programming.html" class="carousel-item">
        <i class="fas fa-cogs"></i>
        <h3>ROS Robotics Programming</h3>
        <p>Robotic manipulation & navigation in a 6-DOF environment using ROS.</p>
      </a>
      <a href="/projects/reaction-wheel-pendulum.html" class="carousel-item">
        <i class="fas fa-balance-scale"></i>
        <h3>Reaction Wheel Pendulum</h3>
        <p>Stabilize a pendulum at its inverted position using reaction wheel dynamics & feedback loops.</p>
      </a>
      <a href="/projects/video-game-sales-analysis.html" class="carousel-item">
        <i class="fas fa-chart-line"></i>
        <h3>Regional Video Games Sales Analysis</h3>
        <p>Statistical modeling to uncover trends in global video game sales across regions.</p>
      </a>
    </div>
    <button class="carousel-btn right" id="nextBtn">&#10095;</button>
  </div>

  <!-- Contact Section -->
  <div class="contact-section">
    <p>Interested in collaborating or have questions? <a href="/about/">Contact me</a>.</p>
  </div>
</div>

<!-- Include Font Awesome CDN for icons -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/js/all.min.js"></script>

<!-- JavaScript for carousel functionality -->
<script>
  const carousel = document.getElementById('projectsCarousel');
  const prevBtn = document.getElementById('prevBtn');
  const nextBtn = document.getElementById('nextBtn');
  
  // Adjust the scroll amount as needed (equal to one card width plus gap)
  const scrollAmount = 260;
  
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
</script>
