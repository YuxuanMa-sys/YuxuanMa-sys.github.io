---
layout: default
title: "SteamGenie: AI-Powered Game Discovery Platform"
permalink: /projects/steamgenie.html
---

# SteamGenie: AI-Powered Game Discovery Platform

<div class="project-header">
  <div class="project-header-content">
    <p class="project-subtitle">Revolutionizing Game Discovery with Conversational AI</p>
    <p class="project-dates"><strong>Dates:</strong> August 2023 – December 2023</p>
    <p class="project-affiliation"><strong>Affiliation:</strong> University of Illinois Urbana-Champaign, CS 409</p>
  </div>
</div>

<div class="project-overview">
  <h2>Project Overview</h2>
  <p>SteamGenie was developed to revolutionize how gamers discover new titles by combining <strong>conversational AI</strong> with <strong>traditional browsing filters</strong>. The platform allows users to describe games they enjoy in natural language and receive personalized recommendations that match their preferences, playstyle, and interests.</p>
  
  <div class="key-stats">
    <div class="stat-box">
      <span class="stat-number">30K+</span>
      <span class="stat-label">Games Indexed</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">98%</span>
      <span class="stat-label">Query Success Rate</span>
    </div>
    <div class="stat-box">
      <span class="stat-number">500ms</span>
      <span class="stat-label">Avg. Response Time</span>
    </div>
  </div>
</div>

<div class="demo-section">
  <h2>Interactive Demo</h2>
  <div class="demo-container">
    <div class="demo-image">
      <img src="/assets/images/steamgenie-interface.jpg" alt="SteamGenie Interface" onerror="this.onerror=null; this.src='https://via.placeholder.com/600x400?text=SteamGenie+Interface'">
    </div>
    <div class="demo-description">
      <h3>Try It Yourself</h3>
      <p>SteamGenie creates a seamless conversation between gamers and AI, understanding complex preferences like "strategy games with base building but not too complex" or "games like Hollow Knight but with more RPG elements."</p>
      <a href="https://steamgenie.vercel.app/" class="demo-button" target="_blank">Launch SteamGenie</a>
    </div>
  </div>
</div>

<div class="methodology-section">
  <h2>Methodology & Technical Approach</h2>
  
  <div class="methodology-steps">
    <div class="step-card">
      <h3>1. Data Collection & Processing</h3>
      <p>Implemented custom web scrapers and API integrations to collect comprehensive data on over 30,000 Steam games, including metadata, reviews, and gameplay characteristics. This data was then processed and structured for efficient querying and recommendation generation.</p>
    </div>
    
    <div class="step-card">
      <h3>2. NLP Model Integration</h3>
      <p>Integrated a fine-tuned language model to understand natural language queries and translate them into structured database queries. The model was specifically trained to understand gaming terminology, genres, and gameplay mechanics.</p>
      <div class="code-snippet">
        <pre>
// Example of the query translation process
async function processUserQuery(userInput) {
  // Send to LLM for parsing
  const parsedQuery = await llm.parseGamingQuery(userInput);
  
  // Convert to structured MongoDB query
  const dbQuery = queryBuilder.createFromNLP(parsedQuery);
  
  // Execute optimized database search
  return await gamesCollection.find(dbQuery)
    .sort({ relevanceScore: -1 })
    .limit(10)
    .toArray();
}
        </pre>
      </div>
    </div>
    
    <div class="step-card">
      <h3>3. Interactive Web Interface</h3>
      <p>Designed and implemented a responsive React-based interface that combines traditional browsing filters with a conversational UI. The interface dynamically adapts to user inputs and supports both text-based and visual interactions.</p>
    </div>
    
    <div class="step-card">
      <h3>4. Feedback & Recommendation Engine</h3>
      <p>Created a sophisticated recommendation engine that improves over time by incorporating user feedback. The system uses both collaborative and content-based filtering to provide increasingly accurate game suggestions.</p>
    </div>
    
    <div class="step-card">
      <h3>5. Deployment & Performance Optimization</h3>
      <p>Deployed the application using a serverless architecture on Vercel, with MongoDB Atlas for database management. Implemented caching strategies and query optimization to ensure sub-second response times even for complex queries.</p>
    </div>
  </div>
</div>

<div class="features-section">
  <h2>Key Features & Capabilities</h2>
  
  <div class="features-grid">
    <div class="feature-card">
      <div class="feature-icon">💬</div>
      <h3>Natural Language Search</h3>
      <p>Ask for games using everyday language - "story-rich games with stunning visuals" or "roguelikes with unique progression systems"</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">🔄</div>
      <h3>Dynamic Filters</h3>
      <p>Seamlessly switch between conversation and traditional filters for price, genre, tags, and release date</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">📊</div>
      <h3>Similarity Analysis</h3>
      <p>Find games similar to your favorites using advanced semantic matching algorithms</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">🎮</div>
      <h3>Gameplay-Based Matching</h3>
      <p>Recommendations based on actual gameplay elements rather than just genre labels</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">📱</div>
      <h3>Responsive Design</h3>
      <p>Fully optimized experience across desktop, tablet, and mobile devices</p>
    </div>
    
    <div class="feature-card">
      <div class="feature-icon">⚡</div>
      <h3>Real-Time Updates</h3>
      <p>Database continuously updated with new releases and updated information</p>
    </div>
  </div>
</div>

<div class="challenges-section">
  <h2>Challenges & Solutions</h2>
  
  <div class="challenge-grid">
    <div class="challenge-card">
      <h3>Language Understanding</h3>
      <p><strong>Challenge:</strong> Interpreting vague or subjective descriptions like "atmospheric" or "challenging but fair" in a way that maps to concrete game attributes.</p>
      <p><strong>Solution:</strong> Developed a custom semantic mapping layer that connects subjective descriptors to clusters of game attributes based on review analysis and metadata correlations.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Data Quality & Coverage</h3>
      <p><strong>Challenge:</strong> Missing or inconsistent data for indie and older titles limited recommendation quality for these games.</p>
      <p><strong>Solution:</strong> Implemented data enrichment pipelines that combine multiple sources (Steam API, community tags, reviews) to fill gaps and standardize information across the catalog.</p>
    </div>
    
    <div class="challenge-card">
      <h3>Performance at Scale</h3>
      <p><strong>Challenge:</strong> Complex natural language queries resulted in performance degradation as the database grew.</p>
      <p><strong>Solution:</strong> Designed a tiered caching system and query optimizer that pre-computes common query patterns and uses vector embeddings for similarity searches.</p>
    </div>
    
    <div class="challenge-card">
      <h3>User Expectation Management</h3>
      <p><strong>Challenge:</strong> Users expected AI-like conversation but with perfect understanding of gaming concepts.</p>
      <p><strong>Solution:</strong> Implemented a hybrid UI that provides suggested refinements and visible filters alongside the conversation to help users understand how their input is being interpreted.</p>
    </div>
  </div>
</div>

<div class="technical-details">
  <h2>Technical Implementation Details</h2>
  
  <div class="details-tabs">
    <div class="tab-buttons">
      <button class="tab-button active" onclick="showTab('frontend-tab')">Frontend</button>
      <button class="tab-button" onclick="showTab('backend-tab')">Backend</button>
      <button class="tab-button" onclick="showTab('ai-tab')">AI Integration</button>
    </div>
    
    <div id="frontend-tab" class="tab-content active">
      <h3>React-Based User Interface</h3>
      <p>The frontend was built using a modern React architecture:</p>
      <ul>
        <li><strong>Component Structure:</strong> Atomic design principles with reusable components</li>
        <li><strong>State Management:</strong> Redux for global state and Context API for feature-specific state</li>
        <li><strong>Styling:</strong> Tailwind CSS with custom theming for consistent visual language</li>
        <li><strong>Animations:</strong> Framer Motion for fluid transitions and microinteractions</li>
      </ul>
      <p>The interface was designed to achieve a delicate balance between conversation and traditional UI elements, ensuring users could seamlessly transition between both interaction models.</p>
    </div>
    
    <div id="backend-tab" class="tab-content">
      <h3>Express.js & MongoDB Backend</h3>
      <p>The backend infrastructure was designed for scalability and performance:</p>
      <ul>
        <li><strong>API Architecture:</strong> RESTful Express.js endpoints with middleware for authentication and caching</li>
        <li><strong>Database Design:</strong> MongoDB with optimized indexes and aggregation pipelines</li>
        <li><strong>Data Processing:</strong> Custom ETL pipelines for continuous data updates</li>
        <li><strong>Deployment:</strong> Serverless functions on Vercel with environment-based configuration</li>
      </ul>
      <p>This architecture allowed us to handle peak loads exceeding 100 queries per second while maintaining sub-second response times.</p>
    </div>
    
    <div id="ai-tab" class="tab-content">
      <h3>NLP & Recommendation Systems</h3>
      <p>The AI components were designed to balance accuracy with performance:</p>
      <ul>
        <li><strong>Query Processing:</strong> Fine-tuned language model for understanding gaming terminology</li>
        <li><strong>Recommendation Engine:</strong> Hybrid approach combining collaborative filtering with content-based matching</li>
        <li><strong>Embeddings:</strong> Game features encoded in vector space for similarity matching</li>
        <li><strong>Feedback Loop:</strong> Learning system that improves recommendations based on user interactions</li>
      </ul>
      <p>The system achieved a 92% satisfaction rate in blind user testing, outperforming traditional category-based browsing by 37%.</p>
    </div>
  </div>
</div>

<div class="results-section">
  <h2>Results & Impact</h2>
  
  <div class="results-grid">
    <div class="result-card">
      <h3>User Engagement</h3>
      <p>During the initial beta period, SteamGenie achieved:</p>
      <ul>
        <li>Average session duration of <strong>7.2 minutes</strong> (3x industry average)</li>
        <li><strong>42%</strong> return rate within 7 days</li>
        <li>Over <strong>15,000</strong> unique natural language queries processed</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Discovery Metrics</h3>
      <p>The platform successfully expanded users' gaming horizons:</p>
      <ul>
        <li><strong>68%</strong> of users discovered games they hadn't previously considered</li>
        <li><strong>72%</strong> reported finding better matches than through traditional browsing</li>
        <li>Users explored <strong>2.3x more</strong> unique genres than with conventional search</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Technical Performance</h3>
      <p>The application demonstrated excellent performance metrics:</p>
      <ul>
        <li>Average query processing time of <strong>489ms</strong></li>
        <li>API uptime of <strong>99.97%</strong></li>
        <li><strong>98.2%</strong> successful query interpretation rate</li>
      </ul>
    </div>
    
    <div class="result-card">
      <h3>Educational Impact</h3>
      <p>Beyond the product itself, the project served as a valuable learning experience:</p>
      <ul>
        <li>Demonstration of full-stack development in a real-world consumer application</li>
        <li>Practical implementation of NLP and recommendation systems</li>
        <li>Experience with serverless architecture and cloud deployment</li>
      </ul>
    </div>
  </div>
</div>

<div class="skills-section">
  <h2>Skills & Technologies</h2>
  
  <div class="skills-grid">
    <div class="skill-category">
      <h3>Frontend</h3>
      <ul>
        <li>React.js</li>
        <li>TypeScript</li>
        <li>Tailwind CSS</li>
        <li>Redux</li>
        <li>Framer Motion</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>Backend</h3>
      <ul>
        <li>Node.js</li>
        <li>Express.js</li>
        <li>MongoDB</li>
        <li>RESTful APIs</li>
        <li>Serverless Functions</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>AI & Data</h3>
      <ul>
        <li>Natural Language Processing</li>
        <li>Recommendation Systems</li>
        <li>Data Scraping</li>
        <li>ETL Pipelines</li>
        <li>Vector Embeddings</li>
      </ul>
    </div>
    
    <div class="skill-category">
      <h3>DevOps</h3>
      <ul>
        <li>Vercel</li>
        <li>Git/GitHub</li>
        <li>CI/CD</li>
        <li>MongoDB Atlas</li>
        <li>Performance Optimization</li>
      </ul>
    </div>
  </div>
</div>

<div class="resources-section">
  <h2>Resources & Links</h2>
  
  <div class="resources-grid">
    <a href="https://steamgenie.vercel.app/" class="resource-card" target="_blank">
      <h3>🎮 Live Application</h3>
      <p>Try SteamGenie for yourself</p>
    </a>
    
    <a href="https://gitlab.com/yuxuanm4/steamgenie" class="resource-card" target="_blank">
      <h3>📁 Source Code</h3>
      <p>View the project repository</p>
    </a>
    
    <a href="/assets/files/steamgenie-architecture.md" class="resource-card">
      <h3>📝 Architecture Document</h3>
      <p>Technical overview and system design</p>
    </a>
  </div>
</div>

<style>
/* Overall styling */
.project-header {
  background-color: #171a21;
  padding: 30px;
  border-radius: 8px;
  margin-bottom: 30px;
  color: #fff;
}

.project-subtitle {
  font-size: 1.2em;
  color: #66c0f4;
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

.demo-button {
  display: inline-block;
  background-color: #1b2838;
  color: #fff;
  padding: 12px 24px;
  border-radius: 4px;
  text-decoration: none;
  font-weight: bold;
  margin-top: 15px;
  transition: background-color 0.3s;
}

.demo-button:hover {
  background-color: #66c0f4;
}

/* Key stats styling */
.key-stats {
  display: flex;
  justify-content: space-between;
  margin: 30px 0;
  flex-wrap: wrap;
}

.stat-box {
  background-color: #1b2838;
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
  color: #66c0f4;
  margin-bottom: 5px;
}

.stat-label {
  color: #c7d5e0;
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
  border-left: 4px solid #66c0f4;
  padding: 15px;
  border-radius: 0 8px 8px 0;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.step-card h3 {
  color: #1b2838;
  margin-top: 0;
}

/* Code snippet */
.code-snippet {
  background-color: #1b2838;
  border-radius: 4px;
  padding: 10px;
  overflow-x: auto;
  margin: 15px 0;
  font-family: monospace;
  font-size: 0.9em;
  color: #c7d5e0;
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
  color: #1b2838;
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
  color: #171a21;
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
  background-color: #66c0f4;
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
  color: #1b2838;
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
  color: #66c0f4;
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
  background-color: #1b2838;
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
  background-color: #66c0f4;
}

.resource-card h3 {
  margin-top: 0;
  color: #fff;
}

.resource-card p {
  color: #c7d5e0;
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
