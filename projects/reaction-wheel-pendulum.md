---
layout: default
title: "Reaction Wheel Pendulum: Inverted Stabilization System"
permalink: /projects/reaction-wheel-pendulum.html
---

<div class="control-project">
  <header class="control-header">
    <div class="control-header-bg"></div>
    <div class="control-header-content">
      <h1>Reaction Wheel Pendulum</h1>
      <div class="control-subtitle">Advanced Control System for Inverted Stabilization</div>
      <div class="control-metadata">
        <div class="control-metadata-item">
          <div class="control-metadata-icon">
            <svg viewBox="0 0 24 24" width="20" height="20">
              <path fill="currentColor" d="M19,4H18V2H16V4H8V2H6V4H5A2,2 0 0,0 3,6V20A2,2 0 0,0 5,22H19A2,2 0 0,0 21,20V6A2,2 0 0,0 19,4M19,20H5V10H19V20M19,8H5V6H19V8Z" />
            </svg>
          </div>
          <div class="control-metadata-text">January 2023 – May 2023</div>
        </div>
        <div class="control-metadata-item">
          <div class="control-metadata-icon">
            <svg viewBox="0 0 24 24" width="20" height="20">
              <path fill="currentColor" d="M12,3L1,9L12,15L21,10.09V17H23V9M5,13.18V17.18L12,21L19,17.18V13.18L12,17L5,13.18Z" />
            </svg>
          </div>
          <div class="control-metadata-text">University of Illinois Urbana-Champaign</div>
        </div>
      </div>
    </div>
  </header>

  <div class="control-intro">
    <div class="control-intro-content">
      <p>This project focuses on the design and implementation of a control system for a Reaction Wheel Pendulum to achieve stabilization at the inverted equilibrium position (180°). The system showcases principles of advanced control theory while addressing real-world challenges of dynamic systems including friction, sensor offsets, and external disturbances.</p>
    </div>
    <div class="control-intro-image">
      <img src="/assets/images/reaction-wheel-pendulum.jpg" alt="Reaction Wheel Pendulum System" onerror="this.onerror=null; this.src='https://via.placeholder.com/400x300?text=Reaction+Wheel+Pendulum'">
    </div>
  </div>

  <div class="control-section">
    <h2>System Dynamics & Mathematical Model</h2>
    <div class="control-math">
      <div class="control-math-diagram">
        <img src="/assets/images/pendulum-diagram.jpg" alt="Pendulum Free Body Diagram" onerror="this.onerror=null; this.src='https://via.placeholder.com/400x300?text=System+Diagram'">
      </div>
      <div class="control-math-equations">
        <div class="control-equation">
          <span class="equation-label">Pendulum Motion:</span>
          <div class="equation-content">
            $$J_p\ddot{\theta}_p + b_p\dot{\theta}_p + mgl\sin(\theta_p) = \tau$$
          </div>
        </div>
        <div class="control-equation">
          <span class="equation-label">Reaction Wheel:</span>
          <div class="equation-content">
            $$J_w\ddot{\theta}_w = -\tau$$
          </div>
        </div>
        <div class="control-equation">
          <span class="equation-label">State-Space Form:</span>
          <div class="equation-content">
            $$\dot{x} = Ax + Bu$$
          </div>
          <div class="equation-notes">
            where $$x = [\theta_p, \dot{\theta}_p, \dot{\theta}_w]^T$$ represents the system state and $$u$$ is the control input
          </div>
        </div>
      </div>
    </div>
    <div class="control-text">
      <p>The dynamics of the reaction wheel pendulum combine the pendulum's rotational motion with the reaction forces from an actuated wheel. The system is inherently unstable at the inverted position, presenting a classic control challenge. We developed a comprehensive mathematical model that accurately captured both the idealized dynamics and the real-world nonlinearities like friction and inertial coupling.</p>
    </div>
  </div>

  <div class="control-section">
    <h2>Control Strategy</h2>
    <div class="control-strategy">
      <div class="control-strategy-item">
        <div class="control-strategy-icon">1</div>
        <div class="control-strategy-content">
          <h3>Linear Quadratic Regulator (LQR)</h3>
          <p>We implemented an LQR controller for the linearized system around the unstable equilibrium point. This approach provided optimal control with respect to the selected cost matrices Q and R, which we tuned to balance performance and energy expenditure.</p>
          <div class="control-code">
            <pre>
% MATLAB Implementation of LQR Controller
A = [0 1 0; g/l 0 0; 0 0 0];  % System matrix
B = [0; -1/J_p; 1/J_w];       % Input matrix

% LQR weight matrices
Q = diag([10, 1, 0.1]);       % State penalty
R = 0.1;                      % Control penalty

% Compute optimal gain matrix
K = lqr(A, B, Q, R);

% Control law
u = -K * x;                   % State feedback control</pre>
          </div>
        </div>
      </div>
      
      <div class="control-strategy-item">
        <div class="control-strategy-icon">2</div>
        <div class="control-strategy-content">
          <h3>Swing-Up Controller</h3>
          <p>For bringing the pendulum from the downward stable position to the upward unstable equilibrium, we designed an energy-based swing-up controller that efficiently pumped energy into the system until it approached the inverted position.</p>
        </div>
      </div>
      
      <div class="control-strategy-item">
        <div class="control-strategy-icon">3</div>
        <div class="control-strategy-content">
          <h3>Friction Compensation</h3>
          <p>To overcome static and dynamic friction effects, we implemented a friction compensation algorithm based on experimental data. This significantly improved the controller's performance, particularly for small angular deviations.</p>
          <div class="control-graph">
            <img src="/assets/images/friction-model.jpg" alt="Friction Model Graph" onerror="this.onerror=null; this.src='https://via.placeholder.com/500x300?text=Friction+Model'">
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="control-section">
    <h2>Implementation & Hardware</h2>
    <div class="control-hardware-grid">
      <div class="control-hardware-item">
        <h3>Motor & Actuation</h3>
        <ul>
          <li>Brushless DC motor with high torque capacity</li>
          <li>Custom motor driver with 20kHz PWM signal</li>
          <li>Aluminum reaction wheel with optimized inertia</li>
        </ul>
      </div>
      <div class="control-hardware-item">
        <h3>Sensing & Feedback</h3>
        <ul>
          <li>High-resolution optical encoder (4096 CPR)</li>
          <li>Real-time angle and velocity calculation</li>
          <li>Software-based state estimation with Kalman filtering</li>
        </ul>
      </div>
      <div class="control-hardware-item">
        <h3>Processing Platform</h3>
        <ul>
          <li>ARM-based microcontroller running at 180MHz</li>
          <li>1kHz control loop sampling frequency</li>
          <li>Interface with MATLAB for data acquisition and analysis</li>
        </ul>
      </div>
      <div class="control-hardware-item">
        <h3>Mechanical Design</h3>
        <ul>
          <li>Precision-machined aluminum components</li>
          <li>Low-friction bearings at the pendulum pivot</li>
          <li>Balanced weight distribution for symmetrical dynamics</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="control-section">
    <h2>Experimental Results</h2>
    <div class="control-results">
      <div class="control-results-graph">
        <img src="/assets/images/pendulum-response.jpg" alt="System Response Graph" onerror="this.onerror=null; this.src='https://via.placeholder.com/800x400?text=System+Response+Graph'">
        <div class="control-caption">System response showing angle stabilization after disturbance at t=5s</div>
      </div>
      <div class="control-results-metrics">
        <div class="control-metric">
          <div class="control-metric-value">±1.2°</div>
          <div class="control-metric-label">Steady-State Error</div>
        </div>
        <div class="control-metric">
          <div class="control-metric-value">0.6s</div>
          <div class="control-metric-label">Response Time</div>
        </div>
        <div class="control-metric">
          <div class="control-metric-value">10%</div>
          <div class="control-metric-label">Disturbance Rejection</div>
        </div>
        <div class="control-metric">
          <div class="control-metric-value">50%</div>
          <div class="control-metric-label">Higher Tolerance</div>
        </div>
      </div>
    </div>
    <div class="control-text">
      <p>Our system achieved robust stabilization at the inverted position, demonstrating 10% higher pivot angle stability and 50% higher disturbance tolerance compared to simpler control designs. The controller could recover from disturbances up to 15° from vertical, and maintain stability indefinitely while compensating for environmental factors.</p>
    </div>
  </div>

  <div class="control-section">
    <h2>Key Challenges & Solutions</h2>
    <div class="control-challenges">
      <div class="control-challenge">
        <h3>Nonlinear Dynamics</h3>
        <p><strong>Challenge:</strong> The pendulum system is inherently nonlinear, particularly away from the equilibrium point.</p>
        <p><strong>Solution:</strong> Implemented a hybrid control approach that used energy-based methods for swing-up and LQR for stabilization near the equilibrium, with a smooth transition between controllers.</p>
      </div>
      <div class="control-challenge">
        <h3>Friction Compensation</h3>
        <p><strong>Challenge:</strong> Static and dynamic friction at the pivot point created dead zones and unpredictable behavior.</p>
        <p><strong>Solution:</strong> Developed an adaptive friction model based on experimental measurements that applied appropriate compensation torque based on velocity and direction.</p>
      </div>
      <div class="control-challenge">
        <h3>Motor Saturation</h3>
        <p><strong>Challenge:</strong> Limited motor torque constrained the controller's ability to respond to large disturbances.</p>
        <p><strong>Solution:</strong> Implemented anti-windup mechanisms and trajectory planning to optimize torque usage while respecting physical limitations.</p>
      </div>
      <div class="control-challenge">
        <h3>Real-time Processing</h3>
        <p><strong>Challenge:</strong> Control algorithms needed to execute within strict timing constraints to maintain stability.</p>
        <p><strong>Solution:</strong> Optimized code implementation with prioritized interrupts and efficient computation to achieve consistent 1kHz control loop frequency.</p>
      </div>
    </div>
  </div>

  <div class="control-section">
    <h2>Skills & Technologies</h2>
    <div class="control-skills">
      <div class="control-skill-category">
        <h3>Control Theory</h3>
        <ul>
          <li>Linear Quadratic Regulator (LQR)</li>
          <li>State Feedback Control</li>
          <li>Stability Analysis</li>
          <li>Nonlinear Control</li>
        </ul>
      </div>
      <div class="control-skill-category">
        <h3>Software Tools</h3>
        <ul>
          <li>MATLAB/Simulink</li>
          <li>Real-time Operating Systems</li>
          <li>Embedded C Programming</li>
          <li>Data Acquisition Systems</li>
        </ul>
      </div>
      <div class="control-skill-category">
        <h3>Hardware Design</h3>
        <ul>
          <li>Mechatronic Systems</li>
          <li>Motor Control</li>
          <li>Sensor Integration</li>
          <li>PCB Design</li>
        </ul>
      </div>
      <div class="control-skill-category">
        <h3>Professional Skills</h3>
        <ul>
          <li>System Modeling</li>
          <li>Experimental Design</li>
          <li>Technical Documentation</li>
          <li>Time Management</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="control-resources">
    <a href="../assets/Pendulum.pdf" class="control-resource" target="_blank">
      <div class="control-resource-icon">
        <svg viewBox="0 0 24 24" width="36" height="36">
          <path fill="currentColor" d="M14,2H6A2,2 0 0,0 4,4V20A2,2 0 0,0 6,22H18A2,2 0 0,0 20,20V8L14,2M18,20H6V4H13V9H18V20Z" />
        </svg>
      </div>
      <div class="control-resource-content">
        <h3>Technical Report</h3>
        <p>Detailed analysis, mathematical derivations, and complete experimental results</p>
      </div>
    </a>
  </div>
</div>

<style>
/* Control Systems Project Styling */
.control-project {
  font-family: 'Inter', 'Roboto', system-ui, -apple-system, sans-serif;
  color: #333;
  max-width: 1200px;
  margin: 0 auto;
  line-height: 1.6;
}

/* Header Styling */
.control-header {
  position: relative;
  padding: 4rem 2rem;
  margin-bottom: 3rem;
  overflow: hidden;
  text-align: center;
}

.control-header-bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
  z-index: -1;
}

.control-header-bg:after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.05'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
}

.control-header-content {
  position: relative;
  z-index: 1;
}

.control-header h1 {
  color: white;
  font-size: 3rem;
  margin: 0 0 0.5rem;
  font-weight: 700;
}

.control-subtitle {
  color: rgba(255, 255, 255, 0.85);
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
}

.control-metadata {
  display: flex;
  justify-content: center;
  gap: 2rem;
  color: rgba(255, 255, 255, 0.7);
}

.control-metadata-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.control-metadata-icon {
  display: flex;
  align-items: center;
}

/* Introduction Section */
.control-intro {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  margin-bottom: 3rem;
  align-items: center;
}

.control-intro-content {
  flex: 1;
  min-width: 300px;
}

.control-intro-content p {
  font-size: 1.1rem;
  margin: 0;
}

.control-intro-image {
  flex: 1;
  min-width: 300px;
  text-align: center;
}

.control-intro-image img {
  max-width: 100%;
  border-radius: 8px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

/* Section Styling */
.control-section {
  margin-bottom: 3rem;
  padding: 0 1rem;
}

.control-section h2 {
  color: #0f2027;
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  position: relative;
  padding-bottom: 0.5rem;
}

.control-section h2:after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 60px;
  height: 3px;
  background: linear-gradient(to right, #203a43, #2c5364);
}

.control-text {
  margin: 1.5rem 0;
}

/* Mathematical Model Section */
.control-math {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  margin: 1rem 0;
  align-items: center;
}

.control-math-diagram {
  flex: 1;
  min-width: 300px;
  text-align: center;
}

.control-math-diagram img {
  max-width: 100%;
  border-radius: 8px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

.control-math-equations {
  flex: 1;
  min-width: 300px;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.control-equation {
  background: #f5f7fa;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
}

.equation-label {
  display: block;
  color: #203a43;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.equation-content {
  font-family: 'Times New Roman', Times, serif;
  font-size: 1.2rem;
  text-align: center;
  padding: 0.5rem 0;
}

.equation-notes {
  font-size: 0.9rem;
  color: #666;
  margin-top: 0.5rem;
}

/* Control Strategy Section */
.control-strategy {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.control-strategy-item {
  display: flex;
  gap: 1.5rem;
}

.control-strategy-icon {
  width: 40px;
  height: 40px;
  background: #2c5364;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  flex-shrink: 0;
}

.control-strategy-content {
  flex: 1;
}

.control-strategy-content h3 {
  margin-top: 0;
  color: #203a43;
  margin-bottom: 1rem;
}

.control-code {
  background: #1e293b;
  border-radius: 8px;
  padding: 1rem;
  margin: 1rem 0;
  overflow-x: auto;
}

.control-code pre {
  margin: 0;
  color: #e2e8f0;
  font-family: 'Courier New', monospace;
  font-size: 0.9rem;
}

.control-graph {
  margin: 1rem 0;
  text-align: center;
}

.control-graph img {
  max-width: 100%;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

/* Hardware Section */
.control-hardware-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1.5rem;
}

.control-hardware-item {
  background: #f5f7fa;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
}

.control-hardware-item h3 {
  margin-top: 0;
  color: #203a43;
  margin-bottom: 1rem;
  font-size: 1.1rem;
  border-bottom: 1px solid #e2e8f0;
  padding-bottom: 0.5rem;
}

.control-hardware-item ul {
  margin: 0;
  padding-left: 1.2rem;
}

.control-hardware-item li {
  margin-bottom: 0.5rem;
  color: #333;
}

/* Results Section */
.control-results {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.control-results-graph {
  width: 100%;
  text-align: center;
}

.control-results-graph img {
  max-width: 100%;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.control-caption {
  font-size: 0.9rem;
  color: #666;
  margin-top: 0.8rem;
}

.control-results-metrics {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  gap: 1rem;
  margin: 1rem 0;
}

.control-metric {
  background: linear-gradient(135deg, #0f2027, #203a43);
  color: white;
  padding: 1.5rem;
  border-radius: 8px;
  text-align: center;
  min-width: 120px;
  flex-grow: 1;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.control-metric-value {
  font-size: 1.8rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.control-metric-label {
  font-size: 0.9rem;
  opacity: 0.9;
}

/* Challenges Section */
.control-challenges {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(400px, 1fr));
  gap: 1.5rem;
}

.control-challenge {
  background: #f5f7fa;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
}

.control-challenge h3 {
  margin-top: 0;
  color: #203a43;
  margin-bottom: 1rem;
}

.control-challenge p {
  margin: 0.5rem 0;
}

.control-challenge strong {
  color: #2c5364;
}

/* Skills Section */
.control-skills {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1.5rem;
}

.control-skill-category {
  background: #f5f7fa;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
}

.control-skill-category h3 {
  margin-top: 0;
  color: #203a43;
  margin-bottom: 1rem;
  font-size: 1.1rem;
  border-bottom: 1px solid #e2e8f0;
  padding-bottom: 0.5rem;
}

.control-skill-category ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

.control-skill-category li {
  margin-bottom: 0.8rem;
  position: relative;
  padding-left: 1.2rem;
  color: #333;
}

.control-skill-category li:before {
  content: "■";
  position: absolute;
  left: 0;
  color: #2c5364;
  font-size: 0.6rem;
  top: 0.4rem;
}

/* Resources Section */
.control-resources {
  margin-top: 3rem;
  margin-bottom: 3rem;
}

.control-resource {
  display: flex;
  gap: 1.5rem;
  background: linear-gradient(135deg, #0f2027, #203a43);
  color: white;
  padding: 1.5rem;
  border-radius: 8px;
  text-decoration: none;
  align-items: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.control-resource:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

.control-resource-icon {
  flex-shrink: 0;
}

.control-resource-content h3 {
  margin-top: 0;
  margin-bottom: 0.5rem;
  color: white;
}

.control-resource-content p {
  margin: 0;
  opacity: 0.9;
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .control-header {
    padding: 3rem 1rem;
  }
  
  .control-header h1 {
    font-size: 2.2rem;
  }
  
  .control-metadata {
    flex-direction: column;
    gap: 1rem;
  }
  
  .control-strategy-item {
    flex-direction: column;
  }
  
  .control-strategy-icon {
    margin-bottom: 1rem;
  }
  
  .control-challenges {
    grid-template-columns: 1fr;
  }
}
</style>

<script>
// Add MathJax for rendering mathematical equations
window.MathJax = {
  tex: {
    inlineMath: [['$', '$']],
    displayMath: [['$$', '$$']]
  },
  svg: {
    fontCache: 'global'
  }
};

// Load MathJax script
document.addEventListener('DOMContentLoaded', function() {
  const script = document.createElement('script');
  script.src = 'https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js';
  script.async = true;
  document.head.appendChild(script);
});
</script>

