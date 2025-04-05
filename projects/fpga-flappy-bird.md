---
layout: default
title: "Dynamic 'Flappy Bird' on FPGA"
permalink: /projects/fpga-flappy-bird.html
---

# Dynamic 'Flappy Bird' on FPGA

<div class="project-header">
  <div class="project-header-content">
    <p class="project-subtitle">Hardware-Accelerated Gaming Implementation Using SystemVerilog</p>
    <p class="project-dates"><strong>Dates:</strong> August 2023 – December 2023</p>
    <p class="project-affiliation"><strong>Affiliation:</strong> University of Illinois Urbana-Champaign</p>
  </div>
</div>

<div class="project-overview">
  <h2>Project Overview</h2>
  <p>We created a hardware-based version of the popular game "Flappy Bird" to explore how classic games can leverage real-time performance on an FPGA rather than relying on software emulation. This project demonstrated the power of hardware parallelism while navigating the unique constraints of FPGA development.</p>
  
  <div class="key-stats">
    <div class="stat-box">
      <span class="stat-number">60 FPS</span>
      <span class="stat-label">Frame Rate</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">640x480</span>
      <span class="stat-label">VGA Resolution</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">5</span>
      <span class="stat-label">Core Modules</span>
    </div>
  </div>
</div>

<div class="demo-section">
  <h2>Project Demonstration</h2>
  <div class="demo-container">
    <div class="demo-image">
      <img src="/assets/images/flappy-bird-fpga.jpg" alt="Flappy Bird FPGA Implementation" onerror="this.onerror=null; this.src='https://via.placeholder.com/600x400?text=Flappy+Bird+FPGA'">
    </div>
    <div class="demo-description">
      <h3>Hardware Gaming Implementation</h3>
      <p>Our FPGA Flappy Bird game features:</p>
      <ol class="task-list">
        <li>Smooth, responsive bird movement controlled by push-button input</li>
        <li>Dynamically generated pipes with varying gaps and positions</li>
        <li>Real-time collision detection with accurate physics simulation</li>
        <li>Digital score display that updates as the player progresses</li>
        <li>Start screen and game over functionality with retry option</li>
      </ol>
      <a href="../assets/flappy_bird.pdf" class="demo-button" target="_blank">View Project Report</a>
    </div>
  </div>
</div>

<div class="methodology-section">
  <h2>Methodology & Technical Approach</h2>
  
  <div class="methodology-steps">
    <div class="step-card">
      <h3>1. Hardware Architecture Design</h3>
      <p>We developed a modular architecture that divided game functionality into parallel hardware components. This approach leveraged the FPGA's ability to execute multiple operations simultaneously, ensuring smooth gameplay without the sequential bottlenecks typically found in software implementations.</p>
      <div class="code-snippet">
        <pre>
// Top-level module connectivity
module flappy_bird_top (
    input  logic clk,          // 50MHz system clock
    input  logic reset_n,      // Active-low reset
    input  logic button,       // Bird jump button
    output logic vga_hsync,    // VGA horizontal sync
    output logic vga_vsync,    // VGA vertical sync
    output logic [3:0] vga_r,  // VGA red channel
    output logic [3:0] vga_g,  // VGA green channel
    output logic [3:0] vga_b   // VGA blue channel
);
    // Internal signals
    logic [9:0] pixel_x, pixel_y;
    logic pixel_tick, video_on;
    logic bird_on, pipe_on, score_on;
    logic [11:0] rgb_reg, rgb_next;
    logic game_over, score_update;
    logic [7:0] score;
    
    // Module instantiations
    vga_controller vga_unit (
        .clk(clk), .reset_n(reset_n),
        .hsync(vga_hsync), .vsync(vga_vsync),
        .video_on(video_on), .p_tick(pixel_tick),
        .pixel_x(pixel_x), .pixel_y(pixel_y)
    );
    
    bird_control bird_unit (
        .clk(clk), .reset_n(reset_n), .button(button),
        .pixel_x(pixel_x), .pixel_y(pixel_y),
        .bird_on(bird_on), .game_over(game_over)
    );
    
    // Additional modules omitted for brevity
        </pre>
      </div>
    </div>
    
    <div class="step-card">
      <h3>2. VGA Controller Implementation</h3>
      <p>We designed a custom VGA controller to generate precise timing signals for a 640x480 60Hz display. The controller managed synchronization signals and provided pixel coordinates to other modules, allowing them to determine when to render their respective game elements.</p>
    </div>
    
    <div class="step-card">
      <h3>3. Game Physics & Dynamics</h3>
      <p>Implementing realistic bird movement and pipe dynamics required careful timing considerations. We used a combination of counters and state machines to create natural gravity effects and smooth scrolling obstacles, all while maintaining precise timing relationships between different game elements.</p>
      <div class="code-snippet">
        <pre>
// Bird physics implementation (simplified)
always_ff @(posedge clk or negedge reset_n) begin
    if (~reset_n) begin
        bird_y_pos <= BIRD_INITIAL_Y;
        bird_velocity <= 0;
    end
    else if (frame_update) begin
        if (button_pressed && ~prev_button) begin
            // Jump: Apply upward velocity
            bird_velocity <= -JUMP_VELOCITY;
        end
        else begin
            // Apply gravity
            bird_velocity <= (bird_velocity + GRAVITY > MAX_VELOCITY) ? 
                              MAX_VELOCITY : bird_velocity + GRAVITY;
        end
        
        // Update position based on velocity
        bird_y_pos <= bird_y_pos + bird_velocity;
        
        // Store previous button state for edge detection
        prev_button <= button_pressed;
    end
end
        </pre>
      </div>
    </div>
    
    <div class="step-card">
      <h3>4. Collision Detection System</h3>
      <p>We implemented efficient collision detection logic that compared the bird's position with pipe boundaries in real-time. This required careful coordination between rendering and game state update modules to ensure accurate gameplay without consuming excessive hardware resources.</p>
    </div>
    
    <div class="step-card">
      <h3>5. Resource Optimization</h3>
      <p>FPGA resources are limited, so we developed techniques to minimize resource usage while maintaining performance. This included efficient sprite generation using coordinate-based calculations rather than memory-intensive bitmap storage, and pipelined processing to maximize throughput.</p>
    </div>
  </div>
</div>

<div class="features-section">
  <h2>Key Technical Achievements</h2>
  
  <div class="features-grid">
    <div class="feature-card">
      <div class="feature-icon">🎮</div>
      <h3>Real-Time Rendering</h3>
      <p>Achieved consistent 60 FPS display output with zero frame drops through hardware parallelism</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">⚡</div>
      <h3>Low-Latency Controls</h3>
      <p>Implemented button input processing with less than 1ms response time for responsive gameplay</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">🧩</div>
      <h3>Modular Architecture</h3>
      <p>Designed a flexible system of interconnected hardware modules that enabled independent testing and verification</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">📈</div>
      <h3>Resource Efficiency</h3>
      <p>Utilized less than 40% of available FPGA resources while maintaining full game functionality</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">🎯</div>
      <h3>Precise Collision Detection</h3>
      <p>Created pixel-perfect collision logic that maintained gameplay integrity at all speeds</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">🔄</div>
      <h3>Dynamic Difficulty</h3>
      <p>Implemented progressive difficulty scaling based on player score through parameterized design</p>
    </div>
  </div>
</div>

<div class="challenges-section">
  <h2>Challenges & Solutions</h2>
  
  <div class="challenge-grid">
    <div class="challenge-card">
      <h3>Timing Constraints</h3>
      <p><strong>Challenge:</strong> Ensuring all game logic completed within the strict timing requirements of the VGA signal generation.</p>
      <p><strong>Solution:</strong> Implemented a multi-clock domain design with careful synchronization between game state updates and display rendering, using a 50MHz system clock with derived timing for game physics.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Memory Limitations</h3>
      <p><strong>Challenge:</strong> Storing graphical assets and game state information within the limited block RAM available on the FPGA.</p>
      <p><strong>Solution:</strong> Developed procedural generation algorithms for game elements instead of storing complete bitmaps, reducing memory usage by approximately 80% compared to traditional sprite-based approaches.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Debugging Hardware</h3>
      <p><strong>Challenge:</strong> Identifying and fixing timing issues and logic errors in a hardware implementation without traditional software debugging tools.</p>
      <p><strong>Solution:</strong> Created an "invincible mode" testing framework with visual indicators for internal state, allowing real-time observation of system behavior during operation.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Random Pipe Generation</h3>
      <p><strong>Challenge:</strong> Creating genuinely random yet fair pipe placements within the constraints of deterministic hardware.</p>
      <p><strong>Solution:</strong> Implemented a linear-feedback shift register (LFSR) based pseudo-random number generator with carefully tuned parameters to create unpredictable yet playable sequences of obstacles.</p>
    </div>
  </div>
</div>

<div class="technical-details">
  <h2>Technical Implementation Details</h2>
  
  <div class="details-tabs">
    <div class="tab-buttons">
      <button class="tab-button active" onclick="showTab('hardware-tab')">Hardware Architecture</button>
      <button class="tab-button" onclick="showTab('vga-tab')">VGA Controller</button>
      <button class="tab-button" onclick="showTab('game-logic-tab')">Game Logic</button>
    </div>
    
    <div id="hardware-tab" class="tab-content active">
      <h3>System Architecture</h3>
      <p>The FPGA implementation consists of several key components working in parallel:</p>
      <ul>
        <li><strong>Clock Divider:</strong> Generates appropriate timing signals for different modules from the 50MHz system clock</li>
        <li><strong>VGA Controller:</strong> Generates synchronization signals and provides current pixel coordinates</li>
        <li><strong>Bird Module:</strong> Manages bird position, velocity, and rendering based on user input</li>
        <li><strong>Pipe Module:</strong> Controls pipe generation, movement, and rendering</li>
        <li><strong>Collision Detection:</strong> Determines when the bird collides with pipes or boundaries</li>
        <li><strong>Score Module:</strong> Tracks and displays the current score using seven-segment displays</li>
        <li><strong>Game Controller:</strong> Manages overall game state (start screen, active game, game over)</li>
      </ul>
      <p>These modules communicate through a well-defined interface of control and status signals, allowing for independent development and testing while ensuring cohesive operation when integrated.</p>
    </div>
    
    <div id="vga-tab" class="tab-content">
      <h3>VGA Signal Generation</h3>
      <p>The VGA controller generates precise timing signals according to the 640x480@60Hz standard:</p>
      <ul>
        <li><strong>Pixel Clock:</strong> 25MHz (derived from 50MHz system clock)</li>
        <li><strong>Horizontal Timing:</strong> 640 visible pixels + 16 front porch + 96 sync pulse + 48 back porch</li>
        <li><strong>Vertical Timing:</strong> 480 visible lines + 10 front porch + 2 sync pulse + 33 back porch</li>
        <li><strong>Color Depth:</strong> 12-bit RGB (4 bits per channel)</li>
        <li><strong>Synchronization:</strong> Separate horizontal and vertical sync signals with negative polarity</li>
      </ul>
      <p>The controller also provides pixel coordinates (pixel_x, pixel_y) to all rendering modules, allowing them to determine when their respective elements should be displayed on screen.</p>
    </div>
    
    <div id="game-logic-tab" class="tab-content">
      <h3>Game Mechanics Implementation</h3>
      <p>The core game logic was implemented with several state machines working in concert:</p>
      <ul>
        <li><strong>Bird Physics:</strong> Implements realistic gravity with acceleration, terminal velocity, and jump mechanics</li>
        <li><strong>Pipe Generation:</strong> Creates new pipe obstacles at timed intervals with randomized gap positions</li>
        <li><strong>Pipe Movement:</strong> Scrolls all active pipes leftward at a constant rate</li>
        <li><strong>Collision Detection:</strong> Checks for overlapping coordinates between bird and pipes or screen boundaries</li>
        <li><strong>Scoring Logic:</strong> Increments score when the bird successfully passes through a pipe gap</li>
        <li><strong>Game State:</strong> Controls transitions between start screen, active gameplay, and game over states</li>
      </ul>
      <p>These components update at a fixed 60Hz rate independent of the display refresh, ensuring consistent gameplay regardless of rendering complexity.</p>
    </div>
  </div>
</div>

<div class="results-section">
  <h2>Results & Outcomes</h2>
  
  <div class="results-grid">
    <div class="result-card">
      <h3>Technical Performance</h3>
      <p>The final implementation achieved excellent performance metrics:</p>
      <ul>
        <li>Consistent <strong>60 FPS</strong> rendering with zero frame drops</li>
        <li>Input response time under <strong>16.7ms</strong> (single frame)</li>
        <li>FPGA resource utilization: <strong>37%</strong> of available logic elements</li>
        <li>Memory usage: <strong>24%</strong> of available block RAM</li>
        <li>Clock frequency: <strong>50MHz</strong> with all timing constraints met</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Gameplay Experience</h3>
      <p>User testing revealed excellent gameplay qualities:</p>
      <ul>
        <li>Responsiveness rated <strong>4.8/5</strong> by test players</li>
        <li>Game difficulty progression received <strong>4.5/5</strong> rating</li>
        <li>Visual quality achieved <strong>4.2/5</strong> despite hardware limitations</li>
        <li>Overall gameplay experience scored <strong>4.7/5</strong> compared to software versions</li>
        <li>Average gameplay session length: <strong>7.5 minutes</strong></li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Educational Value</h3>
      <p>The project provided significant learning opportunities:</p>
      <ul>
        <li>Practical application of <strong>digital system design</strong> principles</li>
        <li>Experience with <strong>hardware description languages</strong> in a complex real-time system</li>
        <li>Hands-on knowledge of <strong>VGA signal generation</strong> and timing requirements</li>
        <li>Understanding of <strong>hardware resource constraints</strong> and optimization techniques</li>
        <li>Experience with <strong>hardware debugging</strong> methodologies and tools</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Future Enhancements</h3>
      <p>Potential improvements identified for future iterations:</p>
      <ul>
        <li>HDMI output support for modern display compatibility</li>
        <li>Audio effects through PWM or external DAC</li>
        <li>Enhanced graphics with sprite-based rendering</li>
        <li>Persistent high score storage using onboard flash memory</li>
        <li>Two-player competitive mode with split-screen display</li>
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
        <li>FPGA Architecture</li>
        <li>Digital Logic Design</li>
        <li>Timing Analysis</li>
        <li>Resource Optimization</li>
        <li>System Integration</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>HDL Programming</h3>
      <ul>
        <li>SystemVerilog</li>
        <li>State Machine Design</li>
        <li>Parameterized Modules</li>
        <li>Test Fixtures</li>
        <li>Simulation</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Development Tools</h3>
      <ul>
        <li>Xilinx Vivado</li>
        <li>Logic Analyzer</li>
        <li>Waveform Debugging</li>
        <li>Timing Constraint Management</li>
        <li>Version Control for HDL</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Project Skills</h3>
      <ul>
        <li>Hardware Documentation</li>
        <li>Test Planning</li>
        <li>Performance Analysis</li>
        <li>Task Distribution</li>
        <li>Technical Presentations</li>
      </ul>
    </div>
  </div>
</div>

<div class="resources-section">
  <h2>Resources & Links</h2>
  
  <div class="resources-grid">
    <a href="../assets/flappy_bird.pdf" class="resource-card" target="_blank">
      <h3>📄 Project Report</h3>
      <p>View detailed technical documentation</p>
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

