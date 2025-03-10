---
layout: default
title: "Home"
---

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

  /* Projects list styling */
  .projects-list {
    margin-top: 2rem;
  }
  .projects-list ul {
    list-style: none;
    padding: 0;
  }
  .projects-list li {
    margin: 1rem 0;
    padding: 1rem;
    border: 1px solid #ddd;
    border-radius: 8px;
    transition: transform 0.2s ease, background-color 0.2s ease;
  }
  .projects-list li:hover {
    transform: translateX(10px);
    background-color: #f9f9f9;
  }
  .projects-list a {
    text-decoration: none;
    color: #2c3e50;
    font-weight: bold;
    font-size: 1.2rem;
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

<div class="home-container">
  <div class="home-hero">
    <h1>Welcome to My Portfolio</h1>
    <p>Discover my favorite projects, learn more about me, and get in touch!</p>
  </div>

  <div class="projects-list">
    <ul>
      <li><a href="/projects/deepseekcoder.html">Enhancing Code Reasoning and Test Generation in DeepSeekCoder (Python)</a></li>
      <li><a href="/projects/reproducibility.html">Reproducibility Research for Research Software</a></li>
      <li><a href="/projects/steamgenie.html">SteamGenie: An Interactive Steam Game Recommendation App</a></li>
      <li><a href="/projects/robotic-task-execution.html">Autonomous Multi-Step Robotic Task Execution System</a></li>
      <li><a href="/projects/habit-forming-keystation.html">Habit-Forming KeyStation</a></li>
      <li><a href="/projects/fpga-flappy-bird.html">Dynamic "Flappy Bird" on FPGA</a></li>
      <li><a href="/projects/ros-robotics-programming.html">ROS Robotics Programming</a></li>
      <li><a href="/projects/reaction-wheel-pendulum.html">Reaction Wheel Pendulum</a></li>
      <li><a href="/projects/video-game-sales-analysis.html">Regional Video Games Sales Analysis</a></li>
    </ul>
  </div>

  <div class="contact-section">
    <p>Interested in collaborating or have questions? <a href="/about/">Contact me</a>.</p>
  </div>
</div>
