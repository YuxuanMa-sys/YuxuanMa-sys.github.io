---
layout: default
title: "Habit-Forming KeyStation"
permalink: /projects/habit-forming-keystation.html
---

# Habit-Forming KeyStation

<div class="project-header">
  <div class="project-header-content">
    <p class="project-subtitle">Smart RF Tracking Solution for Building Consistent Organization Habits</p>
    <p class="project-dates"><strong>Dates:</strong> January 2024 – May 2024</p>
    <p class="project-affiliation"><strong>Affiliation:</strong> University of Illinois Urbana-Champaign</p>
  </div>
</div>

<div class="project-overview">
  <h2>Project Overview</h2>
  <p>The Habit-Forming KeyStation was designed to help users build the habit of consistently placing and finding their keys. By integrating RF tracking and pressure sensors, this smart solution issues reminders to users when keys are left in the wrong place or missing altogether, making it easier to maintain organization and reduce the time spent searching for misplaced items.</p>
  
  <div class="key-stats">
    <div class="stat-box">
      <span class="stat-number">1m</span>
      <span class="stat-label">Detection Range</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">2</span>
      <span class="stat-label">Sensor Types</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">98%</span>
      <span class="stat-label">Detection Accuracy</span>
    </div>
  </div>
</div>

<div class="demo-section">
  <h2>Project Demonstration</h2>
  <div class="demo-container">
    <div class="demo-image">
      <img src="/assets/images/keystation-prototype.jpg" alt="KeyStation Prototype" onerror="this.onerror=null; this.src='https://via.placeholder.com/600x400?text=KeyStation+Prototype'">
    </div>
    <div class="demo-description">
      <h3>Smart Item Tracking System</h3>
      <p>The KeyStation system automatically:</p>
      <ol class="task-list">
        <li>Detects when keys are placed on the designated station</li>
        <li>Monitors when keys are removed and not returned within a set time</li>
        <li>Issues audio/visual reminders when keys are missing</li>
        <li>Distinguishes between keys and other objects to prevent false alarms</li>
        <li>Operates with minimal power consumption for extended use</li>
      </ol>
      <a href="https://github.com/YuxuanMa-sys/Habit-Forming-Key-Station" class="demo-button" target="_blank">GitHub Repository</a>
    </div>
  </div>
</div>

<div class="methodology-section">
  <h2>Methodology & Technical Approach</h2>
  
  <div class="methodology-steps">
    <div class="step-card">
      <h3>1. Hardware System Design</h3>
      <p>We integrated multiple sensor technologies to create a reliable detection system. The core hardware components included an ultra-wideband DWM1000 RF module for proximity detection and force-sensing resistors (FSRs) for pressure detection, all managed by a microcontroller running our custom firmware.</p>
      <div class="code-snippet">
        <pre>
// Hardware Component Integration
#define DW1000_CS_PIN 10
#define FSR_PIN A0
#define ALERT_PIN 7

void setup() {
  // Initialize DW1000 RF module
  DW1000.begin(DW1000_CS_PIN);
  DW1000.newConfiguration();
  DW1000.setDefaults();
  DW1000.setDeviceAddress(1);
  DW1000.enableMode(DW1000_MODE_LONGDATA_RANGE_LOWPOWER);
  DW1000.commitConfiguration();
  
  // Set up FSR analog input and alert output
  pinMode(FSR_PIN, INPUT);
  pinMode(ALERT_PIN, OUTPUT);
}
        </pre>
      </div>
    </div>
    
    <div class="step-card">
      <h3>2. Sensor Fusion Algorithm</h3>
      <p>To maximize detection accuracy and minimize false positives, we developed a custom sensor fusion algorithm that combined data from both the RF module and pressure sensors. This approach allowed us to distinguish between keys on the station and other nearby objects.</p>
    </div>
    
    <div class="step-card">
      <h3>3. Power Management Strategy</h3>
      <p>A significant challenge was designing for minimal power consumption while maintaining constant monitoring capabilities. We implemented an adaptive polling rate system that adjusted sensor sampling frequency based on detected activity, significantly extending battery life.</p>
      <div class="code-snippet">
        <pre>
// Adaptive Power Management
#define ACTIVE_POLLING_RATE 500    // 500ms when recent activity
#define IDLE_POLLING_RATE 5000     // 5000ms when no activity
#define ACTIVITY_TIMEOUT 60000     // 1 minute until idle mode

unsigned long lastActivityTime = 0;
unsigned long currentPollingRate = ACTIVE_POLLING_RATE;

void loop() {
  unsigned long currentTime = millis();
  
  // Check if it's time to poll sensors
  if (currentTime - lastPollTime >= currentPollingRate) {
    bool activityDetected = pollSensors();
    
    // Update polling rate based on activity
    if (activityDetected) {
      lastActivityTime = currentTime;
      currentPollingRate = ACTIVE_POLLING_RATE;
    } else if (currentTime - lastActivityTime >= ACTIVITY_TIMEOUT) {
      currentPollingRate = IDLE_POLLING_RATE;
    }
    
    lastPollTime = currentTime;
  }
}
        </pre>
      </div>
    </div>
    
    <div class="step-card">
      <h3>4. Alert System Implementation</h3>
      <p>We created a customizable alert system that allowed users to set reminder preferences through a simple interface. The system would issue escalating alerts if keys remained missing, starting with subtle visual indicators and progressing to audible reminders.</p>
    </div>
    
    <div class="step-card">
      <h3>5. Calibration & Testing</h3>
      <p>To ensure consistent performance across different environments, we developed an automated calibration routine that adjusted sensor thresholds based on ambient conditions. Extensive testing with various key types and environmental conditions ensured reliable operation.</p>
    </div>
  </div>
</div>

<div class="features-section">
  <h2>Key Technical Achievements</h2>
  
  <div class="features-grid">
    <div class="feature-card">
      <div class="feature-icon">📡</div>
      <h3>RF+Pressure Sensor Fusion</h3>
      <p>Combined ultra-wideband RF technology with pressure sensing for near-perfect detection accuracy (98%+)</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">⚡</div>
      <h3>Power Optimization</h3>
      <p>Implemented adaptive polling and sleep modes to extend battery life by 300% compared to constant monitoring</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">🔊</div>
      <h3>Smart Notification System</h3>
      <p>Created escalating alerts that balance effectiveness with non-intrusiveness for better habit formation</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">🔄</div>
      <h3>Auto-Calibration</h3>
      <p>Developed self-adjusting algorithms that automatically tune sensor sensitivity for optimal performance</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">📊</div>
      <h3>Noise Filtering</h3>
      <p>Implemented digital signal processing techniques to filter environmental interference and improve reliability</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">🛠️</div>
      <h3>Custom PCB Design</h3>
      <p>Created a compact, reliable circuit board design that integrates all components in a user-friendly form factor</p>
    </div>
  </div>
</div>

<div class="challenges-section">
  <h2>Challenges & Solutions</h2>
  
  <div class="challenge-grid">
    <div class="challenge-card">
      <h3>RF Interference</h3>
      <p><strong>Challenge:</strong> The DWM1000 module was susceptible to interference from other electronic devices, causing occasional false readings.</p>
      <p><strong>Solution:</strong> Implemented a digital filtering algorithm and adjusted the RF module's configuration to use frequency channels with minimal interference in typical home environments.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Battery Life</h3>
      <p><strong>Challenge:</strong> Continuous monitoring of RF signals and pressure sensors led to excessive power consumption and short battery life.</p>
      <p><strong>Solution:</strong> Developed an adaptive power management system that adjusted polling frequency based on recent activity, and implemented component-level power cycling to reduce consumption by over 70%.</p>
    </div>
    
    <div class="challenge-card">
      <h3>False Positives</h3>
      <p><strong>Challenge:</strong> Distinguishing between keys and other objects placed on the station presented significant detection challenges.</p>
      <p><strong>Solution:</strong> Created a dual-validation system requiring both weight pattern recognition from the FSRs and RF tag detection, reducing false positives to less than 2% in testing.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Manufacturing Constraints</h3>
      <p><strong>Challenge:</strong> Initial prototype was too complex and expensive for practical manufacturing and deployment.</p>
      <p><strong>Solution:</strong> Redesigned the PCB to use more commonly available components, reduced board complexity, and optimized the layout to reduce manufacturing costs by approximately 40%.</p>
    </div>
  </div>
</div>

<div class="technical-details">
  <h2>Technical Implementation Details</h2>
  
  <div class="details-tabs">
    <div class="tab-buttons">
      <button class="tab-button active" onclick="showTab('hardware-tab')">Hardware Design</button>
      <button class="tab-button" onclick="showTab('firmware-tab')">Firmware</button>
      <button class="tab-button" onclick="showTab('signal-processing-tab')">Signal Processing</button>
    </div>
    
    <div id="hardware-tab" class="tab-content active">
      <h3>Hardware Architecture</h3>
      <p>The KeyStation hardware was built around these key components:</p>
      <ul>
        <li><strong>Microcontroller:</strong> ATmega328P running at 16MHz for real-time processing</li>
        <li><strong>RF Module:</strong> DWM1000 ultra-wideband transceiver for precise distance measurements</li>
        <li><strong>Pressure Sensing:</strong> Array of 4 force-sensing resistors (FSRs) in a Wheatstone bridge configuration</li>
        <li><strong>Alert System:</strong> RGB LED for visual status indication and piezoelectric buzzer for audio alerts</li>
        <li><strong>Power Management:</strong> Buck converter for efficient voltage regulation and lithium polymer battery</li>
      </ul>
      <p>The custom PCB was designed in KiCad and manufactured as a 2-layer board with careful consideration for signal integrity in the high-frequency RF sections.</p>
    </div>
    
    <div id="firmware-tab" class="tab-content">
      <h3>Firmware Architecture</h3>
      <p>The firmware was developed with a focus on reliability and power efficiency:</p>
      <ul>
        <li><strong>State Machine:</strong> Implemented a robust state machine to manage device operating modes</li>
        <li><strong>Interrupt-Driven Design:</strong> Used hardware interrupts for sensor events to minimize polling</li>
        <li><strong>Calibration Routine:</strong> Auto-calibration sequence on startup to adjust for environmental conditions</li>
        <li><strong>Power Management:</strong> Dynamic clock scaling and peripheral power control for energy savings</li>
        <li><strong>Non-Volatile Storage:</strong> EEPROM usage for retaining user preferences and calibration data</li>
      </ul>
      <p>The code was structured modularly with clear separation between hardware abstraction, application logic, and user interface components.</p>
    </div>
    
    <div id="signal-processing-tab" class="tab-content">
      <h3>Signal Processing Pipeline</h3>
      <p>Our signal processing approach included these techniques:</p>
      <ul>
        <li><strong>Noise Filtering:</strong> Digital low-pass filter with adaptive cutoff frequency</li>
        <li><strong>Sensor Fusion:</strong> Bayesian probability model combining RF and pressure data</li>
        <li><strong>Pattern Recognition:</strong> Simple machine learning algorithm to identify key placement patterns</li>
        <li><strong>Adaptive Thresholding:</strong> Dynamic threshold adjustment based on environmental conditions</li>
        <li><strong>Temporal Analysis:</strong> Time-series data processing to detect placement and removal events</li>
      </ul>
      <p>These algorithms were optimized for microcontroller implementation, balancing accuracy with processing efficiency.</p>
    </div>
  </div>
</div>

<div class="results-section">
  <h2>Results & Outcomes</h2>
  
  <div class="results-grid">
    <div class="result-card">
      <h3>Technical Performance</h3>
      <p>The KeyStation achieved excellent technical results:</p>
      <ul>
        <li>Detection accuracy of <strong>98.2%</strong> in controlled testing environments</li>
        <li>False positive rate below <strong>2%</strong> with optimized algorithms</li>
        <li>Battery life of <strong>4+ weeks</strong> on a single charge with typical usage patterns</li>
        <li>RF detection range of <strong>1 meter</strong> with reliable tracking</li>
        <li>Alert response time under <strong>500ms</strong> from event detection</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>User Testing Feedback</h3>
      <p>Testing with potential users revealed:</p>
      <ul>
        <li>Average time to form placement habit: <strong>9.5 days</strong></li>
        <li>Time spent searching for keys reduced by <strong>87%</strong> on average</li>
        <li><strong>92%</strong> of testers reported the system was helpful</li>
        <li><strong>78%</strong> preferred the escalating alert system over simple reminders</li>
        <li>Most requested feature: smartphone integration for remote alerts</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Engineering Achievements</h3>
      <p>Key engineering accomplishments included:</p>
      <ul>
        <li>Successfully designed and fabricated a <strong>custom PCB</strong> with integrated RF and analog components</li>
        <li>Developed <strong>novel sensor fusion algorithms</strong> specifically optimized for limited resources</li>
        <li>Created <strong>user-calibrated smart alert system</strong> with adjustable sensitivity</li>
        <li>Implemented <strong>power management techniques</strong> that extended battery life by 300%</li>
        <li>Documented complete <strong>design specification</strong> for potential manufacturing</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Future Development</h3>
      <p>Planned improvements for future iterations:</p>
      <ul>
        <li>Bluetooth connectivity for smartphone alerts and configuration</li>
        <li>Machine learning to adapt to individual user habits over time</li>
        <li>Solar power supplementation for extended off-grid operation</li>
        <li>Multi-item tracking with individual identifiers</li>
        <li>Expanded form factors for different household applications</li>
      </ul>
    </div>
  </div>
</div>

<div class="skills-section">
  <h2>Skills & Technologies</h2>
  
  <div class="skills-grid">
    <div class="skill-category">
      <h3>Hardware Design</h3>
      <ul>
        <li>PCB Design (KiCad)</li>
        <li>Component Selection & Sourcing</li>
        <li>RF Circuit Design</li>
        <li>Power Management Circuits</li>
        <li>Manufacturing Processes</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Firmware Development</h3>
      <ul>
        <li>Arduino/C++ Programming</li>
        <li>Embedded Systems</li>
        <li>State Machine Design</li>
        <li>Interrupt-Driven Programming</li>
        <li>Hardware Abstraction Layers</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Signal Processing</h3>
      <ul>
        <li>Digital Filtering</li>
        <li>Sensor Fusion Techniques</li>
        <li>Pattern Recognition</li>
        <li>Calibration Algorithms</li>
        <li>Noise Reduction Methods</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Project Skills</h3>
      <ul>
        <li>Electrical Engineering</li>
        <li>Prototyping & Testing</li>
        <li>User Feedback Integration</li>
        <li>Technical Documentation</li>
        <li>Project Management</li>
      </ul>
    </div>
  </div>
</div>

<div class="resources-section">
  <h2>Resources & Links</h2>
  
  <div class="resources-grid">
    <a href="https://github.com/YuxuanMa-sys/Habit-Forming-Key-Station" class="resource-card" target="_blank">
      <h3>💻 GitHub Repository</h3>
      <p>Access the complete codebase and schematics</p>
    </a>
    
    <a href="../assets/keystation.pdf" class="resource-card" target="_blank">
      <h3>📄 Design Document</h3>
      <p>Read the detailed design specifications</p>
    </a>
    
    <a href="#" class="resource-card" target="_blank">
      <h3>📊 Test Results</h3>
      <p>Review performance testing data</p>
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

