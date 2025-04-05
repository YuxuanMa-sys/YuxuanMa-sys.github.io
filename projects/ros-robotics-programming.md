---
layout: default
title: "ROS Robotics Programming: Automated Bridge Construction"
permalink: /projects/ros-robotics-programming.html
---

<div class="ros-project-container">
  <header class="ros-header">
    <h1>ROS Robotics Programming</h1>
    <div class="ros-subtitle">Automated Bridge Construction Using Vision-Based Manipulation</div>
    <div class="ros-meta">
      <span class="ros-meta-item"><i class="fas fa-calendar"></i> January 2023 – May 2023</span>
      <span class="ros-meta-item"><i class="fas fa-university"></i> University of Illinois Urbana-Champaign</span>
    </div>
  </header>

  <div class="ros-video">
    <div class="ros-video-wrapper">
      <div class="ros-video-thumbnail">
        <a href="https://drive.google.com/file/d/188hFCodXZvQx2muQNjZaleoMRTzdldZc/view" target="_blank" rel="noopener noreferrer">
          <img src="/assets/images/robot-bridge-thumbnail.jpg" alt="Robot Building Bridge Demo" 
               onerror="this.onerror=null; this.src='https://via.placeholder.com/800x450?text=ROS+Bridge+Construction+Video'">
          <div class="ros-play-button">
            <svg viewBox="0 0 24 24" width="64" height="64">
              <circle cx="12" cy="12" r="11" fill="#2980b9" stroke="white" stroke-width="1"/>
              <path d="M9.5 7.5v9l7.5-4.5z" fill="white"/>
            </svg>
          </div>
        </a>
      </div>
    </div>
    <div class="ros-video-caption">
      <p>Watch our robot autonomously construct a bridge by detecting, picking, and precisely placing colored blocks.</p>
      <div class="ros-button-group">
        <a href="https://drive.google.com/file/d/188hFCodXZvQx2muQNjZaleoMRTzdldZc/view" class="ros-button" target="_blank">Watch Demo Video</a>
        <a href="../assets/Final_Report.pdf" class="ros-button" target="_blank">Read Full Report</a>
      </div>
    </div>
  </div>

  <section class="ros-overview">
    <h2>Project Overview</h2>
    <p>This project demonstrates the integration of advanced robotics concepts using ROS (Robot Operating System), 
    kinematics, and computer vision to accomplish a complex construction task: building a stable bridge structure 
    through autonomous robotic pick-and-place operations.</p>
    
    <div class="ros-stats">
      <div class="ros-stat">
        <div class="ros-stat-value">232mm</div>
        <div class="ros-stat-label">Bridge Span</div>
      </div>
      <div class="ros-stat">
        <div class="ros-stat-value">3</div>
        <div class="ros-stat-label">Blocks Used</div>
      </div>
      <div class="ros-stat">
        <div class="ros-stat-value">6-DOF</div>
        <div class="ros-stat-label">Robot Arm</div>
      </div>
    </div>
  </section>

  <section class="ros-workflow">
    <h2>Robotic Workflow</h2>
    <div class="ros-workflow-steps">
      <div class="ros-step">
        <div class="ros-step-number">1</div>
        <div class="ros-step-content">
          <h3>Vision-Based Detection</h3>
          <p>Our system uses computer vision to detect multi-colored blocks in the workspace. It calculates 
          the centroid and orientation of each block using marker detection algorithms, providing precise 
          spatial information for the robotic manipulator.</p>
        </div>
      </div>
      
      <div class="ros-step">
        <div class="ros-step-number">2</div>
        <div class="ros-step-content">
          <h3>Path Planning & Kinematics</h3>
          <p>Once blocks are detected, the system computes inverse kinematics to determine the joint angles 
          needed for the robot arm to reach the target positions. We implemented collision-free path planning 
          to ensure safe movement through the workspace.</p>
          <div class="ros-code">
            <pre>
// ROS node for inverse kinematics calculation
void calculateIK(const geometry_msgs::Pose& target_pose, 
                 std::vector<double>& joint_angles) {
  // Convert pose to robot base frame
  tf2::Transform target_tf;
  tf2::fromMsg(target_pose, target_tf);
  
  // Compute inverse kinematics
  KDL::JntArray q_sol;
  int result = ik_solver_->CartToJnt(q_current_, target_tf, q_sol);
  
  if (result < 0) {
    ROS_ERROR("Failed to compute IK solution");
    return;
  }
  
  // Convert solution to joint angles vector
  joint_angles.resize(q_sol.rows());
  for (int i = 0; i < q_sol.rows(); i++) {
    joint_angles[i] = q_sol(i);
  }
}</pre>
          </div>
        </div>
      </div>
      
      <div class="ros-step">
        <div class="ros-step-number">3</div>
        <div class="ros-step-content">
          <h3>Precise Manipulation & Stacking</h3>
          <p>The robotic arm precisely picks up each block and places it at calculated positions to form 
          leaning towers. The system accounts for the specific angle required to create a stable bridge 
          structure, making fine adjustments to ensure structural integrity.</p>
        </div>
      </div>
      
      <div class="ros-step">
        <div class="ros-step-number">4</div>
        <div class="ros-step-content">
          <h3>Bridge Completion</h3>
          <p>After placing the initial blocks at precise angles, the final block is positioned to complete 
          the bridge structure. The system verifies the stability through vision feedback, ensuring the 
          construction remains intact.</p>
        </div>
      </div>
    </div>
  </section>

  <section class="ros-challenges">
    <h2>Technical Challenges & Solutions</h2>
    <div class="ros-challenge-grid">
      <div class="ros-challenge">
        <h3>Camera Calibration</h3>
        <p><strong>Challenge:</strong> Ensuring accurate spatial mapping between camera coordinates and robot coordinates.</p>
        <p><strong>Solution:</strong> Implemented a custom calibration procedure using multiple reference points and homography transformation, achieving sub-centimeter accuracy in workspace mapping.</p>
      </div>
      
      <div class="ros-challenge">
        <h3>Stability Analysis</h3>
        <p><strong>Challenge:</strong> Calculating the precise angles needed for a stable bridge structure.</p>
        <p><strong>Solution:</strong> Developed a physics-based model to determine optimal block placement angles, accounting for center of mass and contact friction to maximize structural stability.</p>
      </div>
      
      <div class="ros-challenge">
        <h3>Gripper Control</h3>
        <p><strong>Challenge:</strong> Maintaining secure grip during manipulation without damaging the blocks.</p>
        <p><strong>Solution:</strong> Fine-tuned gripper force control based on material properties and implemented a slip detection algorithm to adjust grip during movement.</p>
      </div>
      
      <div class="ros-challenge">
        <h3>Environmental Noise</h3>
        <p><strong>Challenge:</strong> Dealing with lighting variations and workspace reflections affecting vision accuracy.</p>
        <p><strong>Solution:</strong> Applied temporal filtering and robust marker detection algorithms that adjust to changing lighting conditions, significantly reducing false positives.</p>
      </div>
    </div>
  </section>

  <section class="ros-technical">
    <h2>ROS Architecture</h2>
    <div class="ros-architecture-diagram">
      <img src="/assets/images/ros-architecture.jpg" alt="ROS System Architecture" 
           onerror="this.onerror=null; this.src='https://via.placeholder.com/800x400?text=ROS+System+Architecture'">
    </div>
    <div class="ros-nodes">
      <h3>Key ROS Nodes & Topics</h3>
      <div class="ros-node-list">
        <div class="ros-node">
          <h4>Camera Node</h4>
          <p>Captures and processes image data, identifying blocks using ArUco marker detection.</p>
          <p><strong>Published Topics:</strong> /camera/image_raw, /detected_markers</p>
        </div>
        
        <div class="ros-node">
          <h4>Motion Planning Node</h4>
          <p>Computes inverse kinematics and generates collision-free trajectories.</p>
          <p><strong>Subscribed Topics:</strong> /detected_markers</p>
          <p><strong>Published Topics:</strong> /robot_trajectory, /gripper_command</p>
        </div>
        
        <div class="ros-node">
          <h4>Robot Control Node</h4>
          <p>Interfaces with the robot hardware, executing planned trajectories and gripper actions.</p>
          <p><strong>Subscribed Topics:</strong> /robot_trajectory, /gripper_command</p>
          <p><strong>Published Topics:</strong> /joint_states, /robot_status</p>
        </div>
        
        <div class="ros-node">
          <h4>Task Manager Node</h4>
          <p>Coordinates the overall bridge-building sequence, managing state transitions and error recovery.</p>
          <p><strong>Subscribed Topics:</strong> /detected_markers, /robot_status</p>
          <p><strong>Published Topics:</strong> /task_state, /visualization_marker</p>
        </div>
      </div>
    </div>
  </section>

  <section class="ros-results">
    <h2>Results & Achievements</h2>
    <div class="ros-results-grid">
      <div class="ros-result">
        <h3>Technical Success</h3>
        <p>Successfully constructed a stable bridge spanning 232mm using three blocks, demonstrating the effectiveness of our vision-guided robotic manipulation system.</p>
      </div>
      
      <div class="ros-result">
        <h3>Algorithm Performance</h3>
        <p>Achieved 95% success rate in marker detection across various lighting conditions, with block placement accuracy within ±2mm of target positions.</p>
      </div>
      
      <div class="ros-result">
        <h3>System Integration</h3>
        <p>Developed a well-integrated ROS framework combining computer vision, motion planning, and robot control into a cohesive system capable of complex assembly tasks.</p>
      </div>
      
      <div class="ros-result">
        <h3>Real-World Application</h3>
        <p>Demonstrated potential applications in automated construction, precision assembly, and robotic manipulation of objects with complex spatial relationships.</p>
      </div>
    </div>
  </section>

  <section class="ros-skills">
    <h2>Skills & Technologies</h2>
    <div class="ros-skills-grid">
      <div class="ros-skill-category">
        <h3>Programming</h3>
        <ul>
          <li>C++</li>
          <li>Python</li>
          <li>CMake</li>
          <li>URDF</li>
        </ul>
      </div>
      
      <div class="ros-skill-category">
        <h3>Robotics</h3>
        <ul>
          <li>Robot Operating System (ROS)</li>
          <li>Inverse Kinematics</li>
          <li>Path Planning</li>
          <li>Control Systems</li>
        </ul>
      </div>
      
      <div class="ros-skill-category">
        <h3>Computer Vision</h3>
        <ul>
          <li>OpenCV</li>
          <li>ArUco Markers</li>
          <li>Camera Calibration</li>
          <li>Image Processing</li>
        </ul>
      </div>
      
      <div class="ros-skill-category">
        <h3>Tools & Frameworks</h3>
        <ul>
          <li>Gazebo Simulation</li>
          <li>MoveIt!</li>
          <li>RViz Visualization</li>
          <li>TF Transformations</li>
        </ul>
      </div>
    </div>
  </section>

  <div class="ros-resources">
    <a href="https://drive.google.com/file/d/188hFCodXZvQx2muQNjZaleoMRTzdldZc/view?usp=sharing" class="ros-resource-link" target="_blank">
      <div class="ros-resource-icon">🎥</div>
      <div class="ros-resource-content">
        <h3>Demo Video</h3>
        <p>Watch the complete bridge construction demonstration</p>
      </div>
    </a>
    
    <a href="../assets/Final_Report.pdf" class="ros-resource-link" target="_blank">
      <div class="ros-resource-icon">📄</div>
      <div class="ros-resource-content">
        <h3>Technical Report</h3>
        <p>Read the detailed project documentation</p>
      </div>
    </a>
  </div>
</div>

<style>
/* ROS Project Styling */
.ros-project-container {
  font-family: 'Roboto', 'Segoe UI', Arial, sans-serif;
  color: #333;
  max-width: 1200px;
  margin: 0 auto;
}

.ros-header {
  text-align: center;
  margin-bottom: 2.5rem;
}

.ros-header h1 {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
  color: #2980b9;
}

.ros-subtitle {
  font-size: 1.3rem;
  color: #2c3e50;
  margin-bottom: 1rem;
}

.ros-meta {
  font-size: 0.95rem;
  color: #34495e;
}

.ros-meta-item {
  display: inline-block;
  margin: 0 10px;
}

/* Video Section */
.ros-video {
  display: flex;
  flex-wrap: wrap;
  margin-bottom: 3rem;
  background: #f5f7fa;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 3px 10px rgba(0,0,0,0.1);
}

.ros-video-wrapper {
  flex: 2;
  min-width: 300px;
  position: relative;
}

.ros-video-thumbnail {
  position: relative;
  width: 100%;
  height: 100%;
  min-height: 200px; /* Fallback for browsers that don't support aspect ratio */
  aspect-ratio: 16/9;
  overflow: hidden;
}

.ros-video-thumbnail img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.ros-video-thumbnail:hover img {
  transform: scale(1.05);
}

.ros-play-button {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: transform 0.2s ease;
  filter: drop-shadow(0px 2px 4px rgba(0,0,0,0.3));
}

.ros-video-thumbnail:hover .ros-play-button {
  transform: translate(-50%, -50%) scale(1.1);
}

.ros-video-wrapper iframe {
  width: 100%;
  height: 100%;
  border: none;
}

.ros-video-caption {
  flex: 1;
  min-width: 250px;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.ros-button-group {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-top: 1rem;
}

.ros-button {
  display: inline-block;
  padding: 10px 20px;
  background: #2980b9;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  font-weight: 500;
  text-align: center;
  transition: background 0.3s, transform 0.2s;
  flex: 1;
  min-width: 100px;
}

.ros-button:hover {
  background: #3498db;
  transform: translateY(-2px);
}

/* Overview Section */
.ros-overview {
  margin-bottom: 3rem;
}

.ros-overview h2 {
  color: #2c3e50;
  font-size: 1.8rem;
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #ecf0f1;
}

.ros-overview p {
  font-size: 1.1rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.ros-stats {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  gap: 20px;
  margin-top: 2rem;
}

.ros-stat {
  text-align: center;
  background: #2980b9;
  color: white;
  padding: 1.5rem;
  border-radius: 10px;
  min-width: 150px;
  box-shadow: 0 3px 10px rgba(0,0,0,0.1);
  flex: 1;
}

.ros-stat-value {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.ros-stat-label {
  font-size: 1rem;
  opacity: 0.9;
}

/* Workflow Section */
.ros-workflow {
  margin-bottom: 3rem;
}

.ros-workflow h2 {
  color: #2c3e50;
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #ecf0f1;
}

.ros-workflow-steps {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.ros-step {
  display: flex;
  gap: 20px;
  background: #f8f9fa;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

.ros-step-number {
  background: #2980b9;
  color: white;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 1.2rem;
  flex-shrink: 0;
}

.ros-step-content h3 {
  margin-top: 0;
  margin-bottom: 0.5rem;
  color: #2c3e50;
}

.ros-step-content p {
  color: #34495e;
}

.ros-code {
  background: #2c3e50;
  border-radius: 5px;
  padding: 1rem;
  margin-top: 1rem;
  overflow-x: auto;
}

.ros-code pre {
  margin: 0;
  color: #ecf0f1;
  font-family: 'Courier New', monospace;
  font-size: 0.9rem;
  white-space: pre-wrap;
}

/* Challenges Section */
.ros-challenges {
  margin-bottom: 3rem;
}

.ros-challenges h2 {
  color: #2c3e50;
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #ecf0f1;
}

.ros-challenge-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(100%, 450px), 1fr));
  gap: 20px;
}

.ros-challenge {
  background: #f8f9fa;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

.ros-challenge h3 {
  margin-top: 0;
  color: #2980b9;
  margin-bottom: 0.75rem;
}

.ros-challenge p {
  margin: 0.5rem 0;
  color: #34495e;
}

.ros-challenge strong {
  color: #2c3e50;
}

/* Technical Section */
.ros-technical {
  margin-bottom: 3rem;
}

.ros-technical h2 {
  color: #2c3e50;
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #ecf0f1;
}

.ros-architecture-diagram {
  margin-bottom: 2rem;
}

.ros-architecture-diagram img {
  width: 100%;
  max-width: 100%;
  border-radius: 8px;
  box-shadow: 0 3px 10px rgba(0,0,0,0.1);
}

.ros-nodes h3 {
  margin-bottom: 1rem;
  color: #2c3e50;
}

.ros-node-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(100%, 450px), 1fr));
  gap: 20px;
}

.ros-node {
  background: #f8f9fa;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

.ros-node h4 {
  margin-top: 0;
  color: #2980b9;
  margin-bottom: 0.75rem;
}

.ros-node p {
  margin: 0.5rem 0;
  font-size: 0.95rem;
  color: #34495e;
}

.ros-node strong {
  color: #2c3e50;
}

/* Results Section */
.ros-results {
  margin-bottom: 3rem;
}

.ros-results h2 {
  color: #2c3e50;
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #ecf0f1;
}

.ros-results-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(100%, 450px), 1fr));
  gap: 20px;
}

.ros-result {
  background: #f8f9fa;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

.ros-result h3 {
  margin-top: 0;
  color: #2980b9;
  margin-bottom: 0.75rem;
}

.ros-result p {
  margin: 0.5rem 0;
  color: #34495e;
}

.ros-result strong {
  color: #2c3e50;
}

/* Skills Section */
.ros-skills {
  margin-bottom: 3rem;
}

.ros-skills h2 {
  color: #2c3e50;
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #ecf0f1;
}

.ros-skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;
}

.ros-skill-category {
  background: #f8f9fa;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

.ros-skill-category h3 {
  margin-top: 0;
  color: #2980b9;
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
  border-bottom: 1px solid #ecf0f1;
}

.ros-skill-category ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.ros-skill-category li {
  margin-bottom: 0.5rem;
  position: relative;
  padding-left: 1.5rem;
  color: #34495e;
}

.ros-skill-category li:before {
  content: "▹";
  color: #2980b9;
  position: absolute;
  left: 0;
  top: 0;
}

/* Resources Section */
.ros-resources {
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
  margin-bottom: 3rem;
}

.ros-resource-link {
  flex: 1;
  min-width: 250px;
  text-decoration: none;
  color: inherit;
  display: flex;
  background: #2980b9;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.3s, box-shadow 0.3s;
}

.ros-resource-link:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

.ros-resource-icon {
  font-size: 2rem;
  background: rgba(0,0,0,0.1);
  padding: 1.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
}

.ros-resource-content {
  padding: 1.5rem;
  flex: 1;
}

.ros-resource-content h3 {
  margin-top: 0;
  margin-bottom: 0.5rem;
  color: white;
}

.ros-resource-content p {
  margin: 0;
  color: rgba(255,255,255,0.9);
  font-size: 0.95rem;
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .ros-header h1 {
    font-size: 2rem;
  }
  
  .ros-subtitle {
    font-size: 1.1rem;
  }
  
  .ros-video {
    flex-direction: column;
  }
  
  .ros-stats {
    flex-direction: column;
  }
  
  .ros-step {
    flex-direction: column;
  }
  
  .ros-step-number {
    margin-bottom: 1rem;
  }
  
  .ros-resources {
    flex-direction: column;
  }
}
</style>  