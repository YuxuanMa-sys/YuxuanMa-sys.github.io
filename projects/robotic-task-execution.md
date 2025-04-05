---
layout: default
title: "ME 446: Robot Dynamics and Control Final Project"
permalink: /projects/robotic-task-execution.html
---

# ME 446: Robot Dynamics and Control Final Project

<div class="project-header">
  <div class="project-header-content">
    <p class="project-subtitle">Multi-Step Robotic Task Execution with Precision Control</p>
    <p class="project-dates"><strong>Dates:</strong> January 2024 – May 2024</p>
    <p class="project-affiliation"><strong>Affiliation:</strong> University of Illinois Urbana-Champaign, ME 446</p>
  </div>
</div>

<div class="project-overview">
  <h2>Project Overview</h2>
  <p>We designed and implemented a comprehensive control system for a robot arm to execute a series of precise tasks requiring careful trajectory planning, force control, and obstacle avoidance. The project demonstrated practical applications of robot dynamics theory in a competitive, real-world scenario.</p>
  
  <div class="key-stats">
    <div class="stat-box">
      <span class="stat-number">5</span>
      <span class="stat-label">Sequential Tasks</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">≤2″</span>
      <span class="stat-label">Peg Insertion Depth</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">500-1000g</span>
      <span class="stat-label">Force Control Range</span>
    </div>
  </div>
</div>

<div class="demo-section">
  <h2>Project Demonstration</h2>
  <div class="demo-container">
    <div class="demo-image">
      <img src="/assets/images/robot-project-demo.jpg" alt="Robot Performing Tasks" onerror="this.onerror=null; this.src='https://via.placeholder.com/600x400?text=Robot+Task+Execution'">
    </div>
    <div class="demo-description">
      <h3>Task Sequence Challenge</h3>
      <p>The robot needed to execute a series of tasks with high precision and reliability:</p>
      <ol class="task-list">
        <li>Move from resting position to a target position in a straight line</li>
        <li>Insert a peg two inches into a hole and hold for at least 0.5 seconds</li>
        <li>Navigate through a zig-zag pattern while avoiding obstacles</li>
        <li>Apply precisely controlled force to an egg (500-1000g for 2+ seconds)</li>
        <li>Return to resting position</li>
      </ol>
      <a href="https://abilkrishna23.wixsite.com/me-446-1" class="demo-button" target="_blank">Project Website</a>
    </div>
  </div>
</div>

<div class="methodology-section">
  <h2>Methodology & Technical Approach</h2>
  
  <div class="methodology-steps">
    <div class="step-card">
      <h3>1. Control System Development</h3>
      <p>We implemented task-space PD control with friction compensation using the Jacobian transpose method. This approach allowed for precise position control while accommodating external forces during operations like peg insertion and egg pressing.</p>
      <div class="code-snippet">
        <pre>
% Task-Space PD Control Implementation
J = calculateJacobian(q);  % Calculate Jacobian at current configuration
F_task = Kp*(x_desired - x_current) + Kd*(xdot_desired - xdot_current);
tau = J'*F_task + compensateFriction(qdot);  % Compute joint torques
        </pre>
      </div>
    </div>
    
    <div class="step-card">
      <h3>2. Trajectory Planning</h3>
      <p>Designed optimal trajectories for each task phase to ensure smooth transitions and minimize jerk. Special attention was given to the obstacle avoidance zig-zag pattern, requiring precise waypoint navigation while maintaining appropriate velocity profiles.</p>
    </div>
    
    <div class="step-card">
      <h3>3. Force Control Strategy</h3>
      <p>For the egg-pressing task, we implemented hybrid position/force control to maintain contact while precisely regulating the applied force. This required careful tuning of control parameters and real-time force feedback processing.</p>
    </div>
    
    <div class="step-card">
      <h4>4. State Machine Implementation</h4>
      <p>Created a robust state machine to manage transitions between different task phases, with appropriate error handling and recovery strategies to ensure task completion even under unexpected conditions.</p>
      <div class="code-snippet">
        <pre>
% State Machine Structure
switch currentState
    case STATE_MOVE_TO_TARGET
        if reachedTarget()
            currentState = STATE_INSERT_PEG;
        end
    case STATE_INSERT_PEG
        if pegInserted() && timer > 0.5
            currentState = STATE_ZIGZAG_NAVIGATION;
        end
    % Additional states for remaining tasks
end
        </pre>
      </div>
    </div>
    
    <div class="step-card">
      <h3>5. Testing & Refinement</h3>
      <p>Conducted extensive testing in both simulation and physical environments, iteratively refining control parameters and trajectory plans based on performance metrics and observed behaviors.</p>
    </div>
  </div>
</div>

<div class="features-section">
  <h2>Key Technical Achievements</h2>
  
  <div class="features-grid">
    <div class="feature-card">
      <div class="feature-icon">🎯</div>
      <h3>Precision Positioning</h3>
      <p>Achieved sub-millimeter positioning accuracy for reliable peg insertion through optimized task-space control</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">⚖️</div>
      <h3>Force Regulation</h3>
      <p>Implemented adaptive force control to maintain pressure within a narrow 500-1000g window for delicate interactions</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">↩️</div>
      <h3>Obstacle Avoidance</h3>
      <p>Navigated complex zig-zag patterns while maintaining smooth velocity profiles and minimizing trajectory errors</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">🔄</div>
      <h3>Task Sequencing</h3>
      <p>Developed a robust state machine architecture that seamlessly transitioned between diverse task requirements</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">📊</div>
      <h3>Real-time Monitoring</h3>
      <p>Created comprehensive data visualization tools for analyzing robot performance during execution</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">⚙️</div>
      <h3>Parameter Optimization</h3>
      <p>Systematically tuned control gains and trajectory parameters to maximize performance across all tasks</p>
    </div>
  </div>
</div>

<div class="challenges-section">
  <h2>Challenges & Solutions</h2>
  
  <div class="challenge-grid">
    <div class="challenge-card">
      <h3>Peg Insertion Precision</h3>
      <p><strong>Challenge:</strong> Achieving reliable peg insertion required extremely precise positioning and approach vectors, with minimal tolerance for error.</p>
      <p><strong>Solution:</strong> Implemented a multi-phase approach strategy with progressively finer control gains as the peg approached the hole, combined with a small search pattern to accommodate minor alignment errors.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Force Sensitivity</h3>
      <p><strong>Challenge:</strong> Maintaining force within the 500-1000g range when pressing the egg required delicate control to avoid exceeding limits or losing contact.</p>
      <p><strong>Solution:</strong> Developed an adaptive force control algorithm that gradually increased pressure while continuously monitoring feedback, with rapid response capabilities to prevent excessive force application.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Trajectory Smoothness</h3>
      <p><strong>Challenge:</strong> The zig-zag pattern navigation required maintaining smooth motion while changing direction multiple times, which risked introducing jerky movements.</p>
      <p><strong>Solution:</strong> Designed cubic spline trajectories with optimized waypoints and velocity profiles to ensure smooth transitions at each direction change point.</p>
    </div>
    
    <div class="challenge-card">
      <h3>System Integration</h3>
      <p><strong>Challenge:</strong> Integrating position control, force regulation, and state management into a cohesive system presented significant complexity.</p>
      <p><strong>Solution:</strong> Adopted a modular architecture with clearly defined interfaces between subsystems, allowing independent development and testing before final integration.</p>
    </div>
  </div>
</div>

<div class="technical-details">
  <h2>Technical Implementation Details</h2>
  
  <div class="details-tabs">
    <div class="tab-buttons">
      <button class="tab-button active" onclick="showTab('control-tab')">Control System</button>
      <button class="tab-button" onclick="showTab('kinematics-tab')">Kinematics</button>
      <button class="tab-button" onclick="showTab('planning-tab')">Motion Planning</button>
    </div>
    
    <div id="control-tab" class="tab-content active">
      <h3>PD Control Implementation</h3>
      <p>Our control approach focused on task-space dynamics with the following key components:</p>
      <ul>
        <li><strong>Proportional-Derivative Control:</strong> Task-space errors mapped to joint torques via the Jacobian transpose</li>
        <li><strong>Friction Compensation:</strong> Model-based compensation for joint friction effects</li>
        <li><strong>Variable Gains:</strong> Adaptive control gains that adjusted based on task phase and proximity to targets</li>
        <li><strong>Force Limitation:</strong> Safety constraints to prevent excessive force application during all phases</li>
      </ul>
      <p>The controller was implemented in MATLAB and executed at 1kHz to ensure responsive operation during critical task phases.</p>
    </div>
    
    <div id="kinematics-tab" class="tab-content">
      <h3>Robot Kinematics & Dynamics</h3>
      <p>We developed a comprehensive kinematic and dynamic model of the robot arm:</p>
      <ul>
        <li><strong>Forward Kinematics:</strong> DH parameter-based model for end-effector position computation</li>
        <li><strong>Inverse Kinematics:</strong> Analytical solution for primary configurations with numerical backup</li>
        <li><strong>Jacobian Calculation:</strong> Efficient computation of the manipulator Jacobian for velocity mapping</li>
        <li><strong>Dynamic Model:</strong> Recursive Newton-Euler formulation for accurate torque estimation</li>
      </ul>
      <p>These models provided the foundation for both the planning and control components, ensuring consistent behavior throughout the task sequence.</p>
    </div>
    
    <div id="planning-tab" class="tab-content">
      <h3>Trajectory Generation</h3>
      <p>Task-specific trajectory planning was crucial for successful execution:</p>
      <ul>
        <li><strong>Linear Segments:</strong> Time-optimal straight-line trajectories for point-to-point movements</li>
        <li><strong>Cubic Splines:</strong> Smooth curved paths for obstacle avoidance sequences</li>
        <li><strong>Blended Transitions:</strong> Velocity-continuous blending between trajectory segments</li>
        <li><strong>Force Trajectories:</strong> Gradual force application profiles for the egg-pressing task</li>
      </ul>
      <p>Each trajectory was verified in simulation prior to physical implementation, with refinements made based on physical testing feedback.</p>
    </div>
  </div>
</div>

<div class="results-section">
  <h2>Results & Outcomes</h2>
  
  <div class="results-grid">
    <div class="result-card">
      <h3>Task Performance</h3>
      <p>The system successfully demonstrated:</p>
      <ul>
        <li>Reliable execution of the complete task sequence with <strong>high repeatability</strong></li>
        <li>Precise peg insertion to the required <strong>two-inch depth</strong></li>
        <li>Consistent force application within the <strong>500-1000g range</strong> during the egg-pressing task</li>
        <li>Smooth navigation through the obstacle course without collisions</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>System Metrics</h3>
      <p>Key performance indicators included:</p>
      <ul>
        <li>Position tracking errors below <strong>2mm</strong> during critical operations</li>
        <li>Force regulation accuracy within <strong>±50g</strong> of target values</li>
        <li>Complete task sequence execution in under <strong>60 seconds</strong></li>
        <li>Successful demonstration over <strong>multiple trials</strong> with consistent results</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Educational Value</h3>
      <p>Through this project, we gained expertise in:</p>
      <ul>
        <li>Practical implementation of robot dynamics and control theory</li>
        <li>Integration of diverse control strategies within a unified framework</li>
        <li>Real-time programming and system optimization techniques</li>
        <li>Systematic testing and troubleshooting methodologies</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Future Work</h3>
      <p>Potential extensions to enhance the system include:</p>
      <ul>
        <li>Implementation of vision-based guidance for increased autonomy</li>
        <li>Advanced impedance control for improved interaction with varying environments</li>
        <li>Machine learning approaches to optimize trajectory parameters automatically</li>
        <li>Integration with ROS for enhanced modularity and extensibility</li>
      </ul>
    </div>
  </div>
</div>

<div class="skills-section">
  <h2>Skills & Technologies</h2>
  
  <div class="skills-grid">
    <div class="skill-category">
      <h3>Robotics</h3>
      <ul>
        <li>Forward/Inverse Kinematics</li>
        <li>Task-Space Control</li>
        <li>Trajectory Planning</li>
        <li>Force Control</li>
        <li>State Machine Design</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Programming</h3>
      <ul>
        <li>MATLAB</li>
        <li>Real-time Control</li>
        <li>Data Visualization</li>
        <li>Algorithm Development</li>
        <li>Embedded Systems</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Engineering</h3>
      <ul>
        <li>System Integration</li>
        <li>Parameter Tuning</li>
        <li>Performance Analysis</li>
        <li>Error Management</li>
        <li>Technical Documentation</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Soft Skills</h3>
      <ul>
        <li>Teamwork</li>
        <li>Problem Solving</li>
        <li>Project Planning</li>
        <li>Time Management</li>
        <li>Technical Presentation</li>
      </ul>
    </div>
  </div>
</div>

<div class="resources-section">
  <h2>Resources & Links</h2>
  
  <div class="resources-grid">
    <a href="https://abilkrishna23.wixsite.com/me-446-1" class="resource-card" target="_blank">
      <h3>🔗 Project Website</h3>
      <p>Visit the official project website</p>
    </a>
    
    <a href="https://abilkrishna23.wixsite.com/me-446-1/demo" class="resource-card" target="_blank">
      <h3>🎥 Video Demonstration</h3>
      <p>Watch the robot in action</p>
    </a>
    
    <a href="https://abilkrishna23.wixsite.com/me-446-1/code" class="resource-card" target="_blank">
      <h3>💻 Code Repository</h3>
      <p>View implementation details</p>
    </a>
  </div>
</div>

<style>
/* Overall styling */
.project-header {
  background-color: #1e3a8a;
  padding: 30px;
  border-radius: 8px;
  margin-bottom: 30px;
  color: #fff;
}

.project-subtitle {
  font-size: 1.2em;
  color: #93c5fd;
  margin-bottom: 10px;
}

.project-overview {
  margin-bottom: 40px;
}

.demo-section {
  margin-bottom: 40px;
}

.demo-container {
  display: flex;
  flex-wrap: wrap;
  gap: 30px;
  align-items: center;
}

.demo-image {
  flex: 1;
  min-width: 300px;
}

.demo-image img {
  width: 100%;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}

.demo-description {
  flex: 1;
  min-width: 300px;
}

.task-list {
  margin-left: 0;
  padding-left: 20px;
}

.task-list li {
  margin-bottom: 8px;
}

.demo-button {
  display: inline-block;
  background-color: #1e3a8a;
  color: #fff;
  padding: 12px 24px;
  border-radius: 4px;
  text-decoration: none;
  font-weight: bold;
  margin-top: 15px;
  transition: background-color 0.3s;
}

.demo-button:hover {
  background-color: #93c5fd;
}

/* Key stats styling */
.key-stats {
  display: flex;
  justify-content: space-between;
  margin: 30px 0;
  flex-wrap: wrap;
}

.stat-box {
  background-color: #1e3a8a;
  border-radius: 8px;
  padding: 20px;
  text-align: center;
  flex: 1;
  margin: 0 10px;
  min-width: 150px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  color: #fff;
}

.stat-number {
  display: block;
  font-size: 2em;
  font-weight: bold;
  color: #93c5fd;
  margin-bottom: 5px;
}

.stat-label {
  color: #dbeafe;
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
  border-left: 4px solid #1e3a8a;
  padding: 15px;
  border-radius: 0 8px 8px 0;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.step-card h3 {
  color: #1e3a8a;
  margin-top: 0;
}

/* Code snippet */
.code-snippet {
  background-color: #1e293b;
  border-radius: 4px;
  padding: 10px;
  overflow-x: auto;
  margin: 15px 0;
  font-family: monospace;
  font-size: 0.9em;
  color: #e2e8f0;
}

.code-snippet pre {
  margin: 0;
  white-space: pre-wrap;
}

/* Features section */
.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.feature-card {
  background-color: #fff;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.feature-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px rgba(0,0,0,0.1);
}

.feature-icon {
  font-size: 2em;
  margin-bottom: 10px;
}

.feature-card h3 {
  color: #1e3a8a;
  margin-top: 0;
  margin-bottom: 10px;
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
  color: #1e3a8a;
  margin-top: 0;
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
  background-color: #1e3a8a;
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

/* Results section */
.results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.result-card {
  background-color: #fff;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.result-card h3 {
  color: #1e3a8a;
  margin-top: 0;
  border-bottom: 1px solid #e1e1e1;
  padding-bottom: 10px;
}

.result-card ul {
  padding-left: 20px;
}

.result-card li {
  margin-bottom: 8px;
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
  color: #1e3a8a;
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
  background-color: #1e3a8a;
  border-radius: 8px;
  padding: 20px;
  text-decoration: none;
  color: #fff;
  transition: transform 0.3s, box-shadow 0.3s;
  display: block;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.resource-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  background-color: #3b82f6;
}

.resource-card h3 {
  margin-top: 0;
  color: #fff;
}

.resource-card p {
  color: #dbeafe;
  margin-bottom: 0;
}

.resource-card:hover p {
  color: #fff;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .key-stats, .challenge-grid, .features-grid, 
  .results-grid, .skills-grid, .resources-grid {
    grid-template-columns: 1fr;
  }
  
  .stat-box {
    margin: 10px 0;
  }
  
  .demo-container {
    flex-direction: column;
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

