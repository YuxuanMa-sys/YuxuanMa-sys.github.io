---
layout: default
title: "Regional Video Games Sales Analysis"
permalink: /projects/video-game-sales-analysis.html
---

<div class="data-science-project">
  <header class="ds-header">
    <div class="ds-header-overlay"></div>
    <div class="ds-header-content">
      <h1>Video Game Sales Analysis</h1>
      <div class="ds-subtitle">Regional Market Insights & Sales Prediction Models</div>
      <div class="ds-metadata">
        <div class="ds-metadata-item">
          <div class="ds-metadata-icon">
            <svg viewBox="0 0 24 24" width="20" height="20">
              <path fill="currentColor" d="M19,4H18V2H16V4H8V2H6V4H5A2,2 0 0,0 3,6V20A2,2 0 0,0 5,22H19A2,2 0 0,0 21,20V6A2,2 0 0,0 19,4M19,20H5V10H19V20M19,8H5V6H19V8Z" />
            </svg>
          </div>
          <div class="ds-metadata-text">January 2022 – May 2022</div>
        </div>
        <div class="ds-metadata-item">
          <div class="ds-metadata-icon">
            <svg viewBox="0 0 24 24" width="20" height="20">
              <path fill="currentColor" d="M12,3L1,9L12,15L21,10.09V17H23V9M5,13.18V17.18L12,21L19,17.18V13.18L12,17L5,13.18Z" />
            </svg>
          </div>
          <div class="ds-metadata-text">University of Illinois Urbana-Champaign</div>
        </div>
      </div>
    </div>
  </header>

  <div class="ds-intro">
    <div class="ds-intro-content">
      <p>This project presents a comprehensive analysis of global video game sales data, exploring the impact of different variables on regional market performance. Using statistical modeling and machine learning techniques, we identified key factors influencing sales across North America, Europe, Japan, and other regions, providing actionable insights for game developers and publishers.</p>
    </div>
    <div class="ds-intro-visual">
      <div class="ds-chart-container">
        <div class="ds-chart-placeholder">
          <img src="/assets/images/data-science-chart.jpg" alt="Video Game Sales Analysis Visualization" onerror="this.onerror=null; this.src='https://via.placeholder.com/500x300?text=Video+Game+Sales+Analysis'">
        </div>
        <div class="ds-chart-caption">Regional sales distribution across game genres and platforms</div>
      </div>
    </div>
  </div>

  <div class="ds-section">
    <h2>Data Analysis Process</h2>
    
    <div class="ds-process-flow">
      <div class="ds-process-step">
        <div class="ds-process-number">1</div>
        <div class="ds-process-content">
          <h3>Data Collection & Preparation</h3>
          <p>The analysis was based on a comprehensive dataset of video game sales across different regions, platforms, and genres. Initial data preparation involved:</p>
          <ul>
            <li>Handling missing values in Year and Publisher columns</li>
            <li>Addressing multicollinearity between predictor variables</li>
            <li>Identifying and managing outliers in sales data</li>
            <li>Creating feature transformations for more accurate modeling</li>
          </ul>
          <div class="ds-code-snippet">
            <pre><code class="language-python">
# Data cleaning example
games_df = games_df.dropna(subset=['Year', 'Publisher'])
games_df['Year'] = games_df['Year'].astype(int)

# Feature engineering
games_df['Total_Sales'] = games_df['NA_Sales'] + games_df['EU_Sales'] + games_df['JP_Sales'] + games_df['Other_Sales']
games_df['Sales_Ratio_NA_EU'] = games_df['NA_Sales'] / games_df['EU_Sales']
            </code></pre>
          </div>
        </div>
      </div>

      <div class="ds-process-step">
        <div class="ds-process-number">2</div>
        <div class="ds-process-content">
          <h3>Exploratory Data Analysis</h3>
          <p>Initial exploration revealed significant regional differences in gaming preferences:</p>
          
          <div class="ds-insights-grid">
            <div class="ds-insight-card">
              <div class="ds-insight-icon">
                <svg viewBox="0 0 24 24" width="24" height="24">
                  <path fill="currentColor" d="M12,5.37L11.56,5.31L6,14.9C6.24,15.11 6.4,15.38 6.47,15.68H17.53C17.6,15.38 17.76,15.11 18,14.9L12.44,5.31L12,5.37Z" />
                  <path fill="currentColor" d="M19,16H5V17A1,1 0 0,0 6,18H18A1,1 0 0,0 19,17V16Z" />
                </svg>
              </div>
              <h4>North America</h4>
              <p>Preference for Action and Sports games, with highest per-title sales average</p>
            </div>
            
            <div class="ds-insight-card">
              <div class="ds-insight-icon">
                <svg viewBox="0 0 24 24" width="24" height="24">
                  <path fill="currentColor" d="M12,5.37L11.56,5.31L6,14.9C6.24,15.11 6.4,15.38 6.47,15.68H17.53C17.6,15.38 17.76,15.11 18,14.9L12.44,5.31L12,5.37Z" />
                  <path fill="currentColor" d="M19,16H5V17A1,1 0 0,0 6,18H18A1,1 0 0,0 19,17V16Z" />
                </svg>
              </div>
              <h4>Europe</h4>
              <p>Strong market for Action and Racing games, with growing indie game popularity</p>
            </div>
            
            <div class="ds-insight-card">
              <div class="ds-insight-icon">
                <svg viewBox="0 0 24 24" width="24" height="24">
                  <path fill="currentColor" d="M12,5.37L11.56,5.31L6,14.9C6.24,15.11 6.4,15.38 6.47,15.68H17.53C17.6,15.38 17.76,15.11 18,14.9L12.44,5.31L12,5.37Z" />
                  <path fill="currentColor" d="M19,16H5V17A1,1 0 0,0 6,18H18A1,1 0 0,0 19,17V16Z" />
                </svg>
              </div>
              <h4>Japan</h4>
              <p>Unique preference for Role-Playing and Strategy games compared to other markets</p>
            </div>
            
            <div class="ds-insight-card">
              <div class="ds-insight-icon">
                <svg viewBox="0 0 24 24" width="24" height="24">
                  <path fill="currentColor" d="M12,5.37L11.56,5.31L6,14.9C6.24,15.11 6.4,15.38 6.47,15.68H17.53C17.6,15.38 17.76,15.11 18,14.9L12.44,5.31L12,5.37Z" />
                  <path fill="currentColor" d="M19,16H5V17A1,1 0 0,0 6,18H18A1,1 0 0,0 19,17V16Z" />
                </svg>
              </div>
              <h4>Other Regions</h4>
              <p>Emerging markets showing diverse tastes, influenced by both Western and Japanese preferences</p>
            </div>
          </div>

          
        </div>
      </div>
    </div>
  </div>

  <div class="ds-section">
    <h2>Statistical Modeling & Analysis</h2>
    
    <div class="ds-model-grid">
      <div class="ds-model-card">
        <div class="ds-model-header">
          <div class="ds-model-icon">
            <svg viewBox="0 0 24 24" width="24" height="24">
              <path fill="currentColor" d="M4,2H20A2,2 0 0,1 22,4V20A2,2 0 0,1 20,22H4A2,2 0 0,1 2,20V4A2,2 0 0,1 4,2M4,4V20H20V4H4M5,13V15H7V13H5M8,13V15H10V13H8M11,13V15H13V13H11M14,13V15H16V13H14M17,13V15H19V13H17M5,16V18H7V16H5M8,16V18H10V16H8M11,16V18H13V16H11M14,16V18H16V16H14M17,16V18H19V16H17M5,10V12H7V10H5M8,10V12H10V10H8M11,10V12H13V10H11M14,10V12H16V10H14M17,10V12H19V10H17M5,7V9H7V7H5M8,7V9H10V7H8M11,7V9H13V7H11M14,7V9H16V7H14M17,7V9H19V7H17Z" />
            </svg>
          </div>
          <h3>LASSO Regression</h3>
        </div>
        <div class="ds-model-description">
          <p>Applied LASSO regression to predict global sales while handling multicollinearity between predictors. The model identified the most influential variables affecting sales performance across regions.</p>
          <div class="ds-model-equation">
            Sales = β₀ + β₁Genre + β₂Platform + β₃Year + ε
          </div>
          <div class="ds-model-metrics">
            <div class="ds-metric">
              <div class="ds-metric-value">0.72</div>
              <div class="ds-metric-label">R² Score</div>
            </div>
            <div class="ds-metric">
              <div class="ds-metric-value">0.68</div>
              <div class="ds-metric-label">Cross-Validation</div>
            </div>
          </div>
        </div>
      </div>
      
      <div class="ds-model-card">
        <div class="ds-model-header">
          <div class="ds-model-icon">
            <svg viewBox="0 0 24 24" width="24" height="24">
              <path fill="currentColor" d="M8,18H11V15H2V13H22V15H13V18H16L12,22L8,18M12,2L8,6H11V9H2V11H22V9H13V6H16L12,2Z" />
            </svg>
          </div>
          <h3>Logistic Regression</h3>
        </div>
        <div class="ds-model-description">
          <p>Implemented logistic regression to classify games by genre, with a focus on predicting role-playing games based on regional sales patterns and platform information.</p>
          <div class="ds-model-equation">
            log(p/(1-p)) = β₀ + β₁NA_Sales + β₂JP_Sales + β₃Platform + ε
          </div>
          <div class="ds-model-metrics">
            <div class="ds-metric">
              <div class="ds-metric-value">0.64</div>
              <div class="ds-metric-label">AUC</div>
            </div>
            <div class="ds-metric">
              <div class="ds-metric-value">76%</div>
              <div class="ds-metric-label">Accuracy</div>
            </div>
          </div>
        </div>
      </div>
      
      <div class="ds-model-card">
        <div class="ds-model-header">
          <div class="ds-model-icon">
            <svg viewBox="0 0 24 24" width="24" height="24">
              <path fill="currentColor" d="M22,21H2V3H4V19H6V10H10V19H12V6H16V19H18V14H22V21Z" />
            </svg>
          </div>
          <h3>Hypothesis Testing</h3>
        </div>
        <div class="ds-model-description">
          <p>Conducted statistical tests to identify significant differences in regional preferences, with particular focus on Japan's unique market characteristics compared to Western regions.</p>
          <div class="ds-model-equation">
            H₀: μ₁ = μ₂ vs H₁: μ₁ ≠ μ₂
          </div>
          <div class="ds-model-metrics">
            <div class="ds-metric">
              <div class="ds-metric-value">&lt;0.001</div>
              <div class="ds-metric-label">p-value</div>
            </div>
            <div class="ds-metric">
              <div class="ds-metric-value">95%</div>
              <div class="ds-metric-label">Confidence Level</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="ds-section">
    <h2>Key Findings & Business Insights</h2>
    
    <div class="ds-findings">
      <div class="ds-finding-item">
        <div class="ds-finding-number">01</div>
        <div class="ds-finding-content">
          <h3>Regional Market Differences</h3>
          <p>The Japanese market showed statistically significant preference for Role-Playing and Strategy games compared to North America and Europe. This cultural difference should inform region-specific game development and marketing strategies.</p>
          <div class="ds-highlight-box">
            <strong>Key Insight:</strong> Games that performed well in Japan showed 68% lower correlation with North American sales compared to European sales.
          </div>
        </div>
      </div>
      
      <div class="ds-finding-item">
        <div class="ds-finding-number">02</div>
        <div class="ds-finding-content">
          <h3>Platform Influence</h3>
          <p>Platform choice significantly impacts sales potential, with console exclusives showing different regional penetration rates. Mobile gaming showed a growing trend in the data, though traditional console platforms still dominated total sales volume.</p>
          <div class="ds-highlight-box">
            <strong>Key Insight:</strong> Nintendo platforms showed 2.3x higher sales in Japan compared to other regions for similar titles.
          </div>
        </div>
      </div>
      
      <div class="ds-finding-item">
        <div class="ds-finding-number">03</div>
        <div class="ds-finding-content">
          <h3>Temporal Trends</h3>
          <p>Analysis of year-over-year data revealed shifting genre preferences and platform adoption rates. Genre popularity showed cyclical patterns, with certain genres experiencing resurgence after periods of decline.</p>
          <div class="ds-highlight-box">
            <strong>Key Insight:</strong> Action games maintained consistent popularity across all regions throughout the time period studied.
          </div>
        </div>
      </div>
    </div>
    
    <div class="ds-visualization">
      
      <div class="ds-visualization-caption">
        Heatmap showing correlation between game attributes and regional sales performance
      </div>
    </div>
  </div>

  <div class="ds-section">
    <h2>Business Applications & Future Work</h2>
    
    <div class="ds-applications-grid">
      <div class="ds-application-card">
        <h3>Publisher Strategy</h3>
        <p>Publishers can use these insights to optimize marketing budget allocation across regions based on genre and platform, potentially increasing ROI by targeting the right audience with appropriate messaging.</p>
      </div>
      
      <div class="ds-application-card">
        <h3>Game Development</h3>
        <p>Development studios can tailor game mechanics and themes to better target specific regional markets, incorporating cultural preferences identified through the statistical analysis.</p>
      </div>
      
      <div class="ds-application-card">
        <h3>Platform Holders</h3>
        <p>Console manufacturers and digital storefronts can use these insights to curate region-specific promotions and exclusivity deals that match local market preferences.</p>
      </div>
      
      <div class="ds-application-card">
        <h3>Market Expansion</h3>
        <p>Companies looking to expand into new territories can leverage the predictive models to estimate potential sales and identify the most promising genres and platforms for each region.</p>
      </div>
    </div>
    
    <div class="ds-future-work">
      <h3>Future Research Directions</h3>
      <ul>
        <li>Incorporate pricing data to analyze price elasticity across different markets</li>
        <li>Expand the analysis to include digital sales and free-to-play monetization models</li>
        <li>Develop time series forecasting to predict emerging genre trends by region</li>
        <li>Include additional variables such as marketing spend and critical reception</li>
      </ul>
    </div>
  </div>

  <div class="ds-skills-section">
    <h2>Technical Skills & Tools</h2>
    
    <div class="ds-skills-grid">
      <div class="ds-skill-category">
        <h3>Programming</h3>
        <ul>
          <li>Python</li>
          <li>Pandas</li>
          <li>NumPy</li>
          <li>Jupyter Notebooks</li>
        </ul>
      </div>
      
      <div class="ds-skill-category">
        <h3>Statistical Analysis</h3>
        <ul>
          <li>Hypothesis Testing</li>
          <li>Regression Analysis</li>
          <li>Classification Models</li>
          <li>Feature Selection</li>
        </ul>
      </div>
      
      <div class="ds-skill-category">
        <h3>Data Visualization</h3>
        <ul>
          <li>Matplotlib</li>
          <li>Seaborn</li>
          <li>Heatmaps</li>
          <li>Interactive Charts</li>
        </ul>
      </div>
      
      <div class="ds-skill-category">
        <h3>Machine Learning</h3>
        <ul>
          <li>Scikit-learn</li>
          <li>LASSO Regularization</li>
          <li>Logistic Regression</li>
          <li>Cross-Validation</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="ds-resources">
    <a href="https://github.com/YuxuanMa-sys/Data-Science-Exploration/blob/main/Final%20Exam.ipynb" class="ds-resource-link" target="_blank">
      <div class="ds-resource-icon">
        <svg viewBox="0 0 24 24" width="36" height="36">
          <path fill="currentColor" d="M12,2A10,10 0 0,0 2,12C2,16.42 4.87,20.17 8.84,21.5C9.34,21.58 9.5,21.27 9.5,21C9.5,20.77 9.5,20.14 9.5,19.31C6.73,19.91 6.14,17.97 6.14,17.97C5.68,16.81 5.03,16.5 5.03,16.5C4.12,15.88 5.1,15.9 5.1,15.9C6.1,15.97 6.63,16.93 6.63,16.93C7.5,18.45 8.97,18 9.54,17.76C9.63,17.11 9.89,16.67 10.17,16.42C7.95,16.17 5.62,15.31 5.62,11.5C5.62,10.39 6,9.5 6.65,8.79C6.55,8.54 6.2,7.5 6.75,6.15C6.75,6.15 7.59,5.88 9.5,7.17C10.29,6.95 11.15,6.84 12,6.84C12.85,6.84 13.71,6.95 14.5,7.17C16.41,5.88 17.25,6.15 17.25,6.15C17.8,7.5 17.45,8.54 17.35,8.79C18,9.5 18.38,10.39 18.38,11.5C18.38,15.32 16.04,16.16 13.81,16.41C14.17,16.72 14.5,17.33 14.5,18.26C14.5,19.6 14.5,20.68 14.5,21C14.5,21.27 14.66,21.59 15.17,21.5C19.14,20.16 22,16.42 22,12A10,10 0 0,0 12,2Z" />
        </svg>
      </div>
      <div class="ds-resource-content">
        <h3>Project Notebook on GitHub</h3>
        <p>View the full data analysis, code implementation, and detailed methodology</p>
      </div>
    </a>
  </div>
</div>

<style>
/* Data Science Project Styling */
.data-science-project {
  font-family: 'Inter', 'Roboto', system-ui, -apple-system, sans-serif;
  color: #333;
  max-width: 1200px;
  margin: 0 auto;
  line-height: 1.6;
}

/* Header Styling */
.ds-header {
  position: relative;
  padding: 4rem 2rem;
  margin-bottom: 3rem;
  overflow: hidden;
  text-align: center;
}

.ds-header-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
  opacity: 0.85;
  z-index: -1;
}

.ds-header-content {
  position: relative;
  z-index: 1;
}

.ds-header h1 {
  color: white;
  font-size: 3rem;
  margin: 0 0 0.5rem;
  font-weight: 700;
}

.ds-subtitle {
  color: rgba(255, 255, 255, 0.9);
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
}

.ds-metadata {
  display: flex;
  justify-content: center;
  gap: 2rem;
  color: rgba(255, 255, 255, 0.8);
}

.ds-metadata-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.ds-metadata-icon {
  display: flex;
  align-items: center;
}

/* Introduction Section */
.ds-intro {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  margin-bottom: 3rem;
  align-items: center;
  padding: 0 1.5rem;
}

.ds-intro-content {
  flex: 1;
  min-width: 300px;
}

.ds-intro-content p {
  font-size: 1.1rem;
  margin: 0;
}

.ds-intro-visual {
  flex: 1;
  min-width: 300px;
}

.ds-chart-container {
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

.ds-chart-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.ds-chart-placeholder img {
  width: 100%;
  height: auto;
}

.ds-chart-caption {
  padding: 1rem;
  text-align: center;
  font-size: 0.9rem;
  color: #666;
  border-top: 1px solid #eee;
}

/* Section Styling */
.ds-section {
  margin-bottom: 3rem;
  padding: 0 1.5rem;
}

.ds-section h2 {
  color: #1a2a6c;
  font-size: 1.8rem;
  margin-bottom: 1.5rem;
  position: relative;
  padding-bottom: 0.5rem;
}

.ds-section h2:after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 60px;
  height: 3px;
  background: linear-gradient(to right, #1a2a6c, #b21f1f);
}

/* Process Flow Styling */
.ds-process-flow {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
  margin-top: 2rem;
}

.ds-process-step {
  display: flex;
  gap: 1.5rem;
}

.ds-process-number {
  width: 40px;
  height: 40px;
  background: linear-gradient(135deg, #1a2a6c, #b21f1f);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: 700;
  flex-shrink: 0;
}

.ds-process-content {
  flex: 1;
}

.ds-process-content h3 {
  margin-top: 0;
  color: #1a2a6c;
  margin-bottom: 1rem;
  font-size: 1.3rem;
}

.ds-process-content ul {
  margin: 1rem 0;
  padding-left: 1.5rem;
}

.ds-process-content li {
  margin-bottom: 0.5rem;
}

/* Code Snippet Styling */
.ds-code-snippet {
  background: #282c34;
  border-radius: 8px;
  padding: 1rem;
  margin: 1rem 0;
  overflow-x: auto;
}

.ds-code-snippet pre {
  margin: 0;
}

.ds-code-snippet code {
  font-family: 'Fira Code', 'Courier New', monospace;
  font-size: 0.9rem;
  color: #abb2bf;
}

/* Insights Grid Styling */
.ds-insights-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 1.5rem;
  margin: 1.5rem 0;
}

.ds-insight-card {
  background: #f8f9fa;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.ds-insight-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.ds-insight-icon {
  color: #1a2a6c;
  margin-bottom: 1rem;
}

.ds-insight-card h4 {
  margin: 0 0 0.5rem;
  color: #1a2a6c;
  font-size: 1.1rem;
}

.ds-insight-card p {
  margin: 0;
  font-size: 0.9rem;
  color: #555;
}

/* Graph Styling */
.ds-graph {
  margin: 2rem 0;
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.ds-graph img {
  width: 100%;
  height: auto;
  display: block;
}

.ds-graph-caption {
  padding: 1rem;
  text-align: center;
  font-size: 0.9rem;
  color: #666;
  border-top: 1px solid #eee;
}

/* Model Grid Styling */
.ds-model-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}

.ds-model-card {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.ds-model-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.12);
}

.ds-model-header {
  background: linear-gradient(135deg, #1a2a6c, #b21f1f);
  color: white;
  padding: 1.5rem;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.ds-model-icon {
  display: flex;
  align-items: center;
}

.ds-model-header h3 {
  margin: 0;
  font-size: 1.2rem;
}

.ds-model-description {
  padding: 1.5rem;
}

.ds-model-description p {
  margin: 0 0 1rem;
  color: #555;
}

.ds-model-equation {
  background: #f5f7fa;
  padding: 1rem;
  border-radius: 4px;
  text-align: center;
  font-family: 'Times New Roman', Times, serif;
  font-style: italic;
  margin-bottom: 1.5rem;
}

.ds-model-metrics {
  display: flex;
  justify-content: space-around;
}

.ds-metric {
  text-align: center;
}

.ds-metric-value {
  font-size: 1.8rem;
  font-weight: 700;
  color: #1a2a6c;
}

.ds-metric-label {
  font-size: 0.85rem;
  color: #666;
}

/* Findings Styling */
.ds-findings {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  margin: 2rem 0;
}

.ds-finding-item {
  display: flex;
  gap: 1.5rem;
}

.ds-finding-number {
  font-size: 2.5rem;
  font-weight: 800;
  color: #1a2a6c;
  opacity: 0.6;
  line-height: 1;
  flex-shrink: 0;
}

.ds-finding-content {
  flex: 1;
}

.ds-finding-content h3 {
  margin-top: 0;
  color: #1a2a6c;
  margin-bottom: 1rem;
  font-size: 1.3rem;
}

.ds-highlight-box {
  background: #f8f9fa;
  border-left: 3px solid #b21f1f;
  padding: 1rem;
  margin-top: 1rem;
  font-size: 0.95rem;
}

/* Visualization Styling */
.ds-visualization {
  margin: 3rem 0;
}

.ds-visualization-container {
  background: white;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.ds-visualization-container img {
  width: 100%;
  height: auto;
  display: block;
}

.ds-visualization-caption {
  margin-top: 1rem;
  text-align: center;
  font-size: 0.9rem;
  color: #666;
}

/* Applications Grid Styling */
.ds-applications-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
  margin: 2rem 0;
}

.ds-application-card {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
}

.ds-application-card h3 {
  margin-top: 0;
  color: #1a2a6c;
  margin-bottom: 1rem;
  font-size: 1.2rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #f0f0f0;
}

.ds-application-card p {
  margin: 0;
  color: #555;
}

/* Future Work Styling */
.ds-future-work {
  background: #f8f9fa;
  border-radius: 8px;
  padding: 1.5rem;
  margin-top: 2rem;
}

.ds-future-work h3 {
  margin-top: 0;
  color: #1a2a6c;
  margin-bottom: 1rem;
  font-size: 1.2rem;
}

.ds-future-work ul {
  margin: 0;
  padding-left: 1.5rem;
}

.ds-future-work li {
  margin-bottom: 0.8rem;
  color: #555;
}

/* Skills Section Styling */
.ds-skills-section {
  margin: 3rem 0;
  padding: 2rem 1.5rem;
  background: linear-gradient(135deg, rgba(26, 42, 108, 0.05), rgba(178, 31, 31, 0.05));
  border-radius: 8px;
}

.ds-skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 1.5rem;
  margin-top: 1.5rem;
}

.ds-skill-category {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
}

.ds-skill-category h3 {
  margin-top: 0;
  color: #1a2a6c;
  margin-bottom: 1rem;
  font-size: 1.1rem;
  border-bottom: 1px solid #eee;
  padding-bottom: 0.5rem;
}

.ds-skill-category ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

.ds-skill-category li {
  margin-bottom: 0.8rem;
  position: relative;
  padding-left: 1.2rem;
  color: #555;
}

.ds-skill-category li:before {
  content: "•";
  position: absolute;
  left: 0;
  color: #b21f1f;
  font-size: 1.2rem;
  line-height: 1;
}

/* Resources Styling */
.ds-resources {
  margin: 3rem 0;
}

.ds-resource-link {
  display: flex;
  gap: 1.5rem;
  background: linear-gradient(135deg, #1a2a6c, #b21f1f);
  color: white;
  padding: 1.5rem;
  border-radius: 8px;
  text-decoration: none;
  align-items: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.ds-resource-link:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.ds-resource-icon {
  flex-shrink: 0;
}

.ds-resource-content h3 {
  margin-top: 0;
  margin-bottom: 0.5rem;
  color: white;
  font-size: 1.3rem;
}

.ds-resource-content p {
  margin: 0;
  color: rgba(255, 255, 255, 0.8);
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .ds-header {
    padding: 3rem 1rem;
  }
  
  .ds-header h1 {
    font-size: 2.2rem;
  }
  
  .ds-metadata {
    flex-direction: column;
    gap: 1rem;
    align-items: center;
  }
  
  .ds-finding-item,
  .ds-process-step {
    flex-direction: column;
    gap: 0.5rem;
  }
  
  .ds-finding-number {
    font-size: 2rem;
  }
  
  .ds-process-number {
    margin-bottom: 0.5rem;
  }
  
  .ds-model-metrics {
    flex-direction: column;
    gap: 1rem;
  }
}
</style>

