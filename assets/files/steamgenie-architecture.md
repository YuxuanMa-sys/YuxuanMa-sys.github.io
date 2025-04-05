---
layout: default
title: "SteamGenie Architecture Document"
permalink: /assets/files/steamgenie-architecture.html
---

<style>
/* Document styling to match SteamGenie visual theme */
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  line-height: 1.6;
  color: #333;
}

/* Architecture header */
.architecture-header {
  background-color: #171a21;
  color: #fff;
  padding: 30px;
  border-radius: 8px;
  margin-bottom: 30px;
}

.architecture-header h1 {
  color: #fff;
  margin-top: 0;
  margin-bottom: 20px;
}

.architecture-meta {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px 20px;
}

.architecture-meta p {
  margin: 0;
  color: #c7d5e0;
}

/* Table of Contents */
.toc-container {
  background-color: #f8f9fa;
  border-radius: 8px;
  padding: 20px;
  margin-bottom: 30px;
}

.toc-list {
  padding-left: 20px;
}

.toc-list li {
  margin-bottom: 8px;
}

.toc-list a {
  color: #1b2838;
  text-decoration: none;
  font-weight: 500;
}

.toc-list a:hover {
  color: #66c0f4;
  text-decoration: underline;
}

/* Sections */
.section {
  margin-bottom: 50px;
}

.section h2 {
  color: #1b2838;
  border-bottom: 2px solid #66c0f4;
  padding-bottom: 8px;
  margin-bottom: 20px;
}

.subsection {
  margin-bottom: 30px;
}

.subsection h3 {
  color: #1b2838;
  font-weight: 600;
  margin-bottom: 15px;
}

/* Definition table */
.definitions-table {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 10px;
  margin-top: 15px;
}

.definition-item {
  display: flex;
  background-color: #f8f9fa;
  border-radius: 4px;
  overflow: hidden;
}

.term {
  font-weight: bold;
  background-color: #1b2838;
  color: #fff;
  padding: 10px;
  min-width: 80px;
  text-align: center;
}

.definition {
  padding: 10px;
  flex: 1;
}

/* Overview tiers */
.overview-tiers {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  margin: 20px 0;
}

.tier-card {
  flex: 1;
  min-width: 200px;
  background-color: #f8f9fa;
  border-left: 4px solid #66c0f4;
  padding: 15px;
  border-radius: 0 4px 4px 0;
}

.tier-card h4 {
  margin-top: 0;
  margin-bottom: 8px;
  color: #1b2838;
}

.tier-card p {
  margin: 0;
}

/* Context diagram */
.context-diagram {
  background-color: #1b2838;
  border-radius: 8px;
  padding: 20px;
  margin: 20px 0;
  overflow-x: auto;
}

.diagram {
  color: #c7d5e0;
  font-family: monospace;
  white-space: pre;
  font-size: 14px;
  margin: 0;
}

/* Principles grid */
.principles-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 15px;
  margin-top: 20px;
}

.principle-card {
  background-color: #f8f9fa;
  border-radius: 8px;
  padding: 15px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}

.principle-card h4 {
  color: #1b2838;
  margin-top: 0;
  margin-bottom: 8px;
  font-size: 1em;
}

.principle-card p {
  margin: 0;
  font-size: 0.9em;
  color: #666;
}

/* Component section */
.component-section {
  margin-bottom: 25px;
}

.component-section h4 {
  color: #1b2838;
  margin-bottom: 15px;
}

/* Code blocks */
.code-block {
  background-color: #1b2838;
  border-radius: 8px;
  padding: 15px;
  overflow-x: auto;
  margin: 15px 0;
}

.code-block pre {
  margin: 0;
  color: #c7d5e0;
  font-family: 'Courier New', Courier, monospace;
  font-size: 14px;
}

.code-block.json pre {
  color: #afd4ee;
}

/* Feature lists */
.feature-list {
  padding-left: 20px;
  margin: 15px 0;
}

.feature-list li {
  margin-bottom: 8px;
}

.feature-highlight {
  color: #1b2838;
  font-weight: bold;
}

/* API modules grid */
.api-modules-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 15px;
  margin: 15px 0;
}

.api-module-card {
  background-color: #f8f9fa;
  border-radius: 8px;
  padding: 15px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}

.api-module-card h5 {
  color: #1b2838;
  margin-top: 0;
  margin-bottom: 8px;
  font-size: 1em;
}

.api-module-card p {
  margin: 0;
  font-size: 0.9em;
  color: #666;
}

/* Schema section */
.schema-section {
  margin-bottom: 25px;
}

.schema-section h4 {
  color: #1b2838;
  margin-bottom: 15px;
}

/* Data flow */
.data-flow-container {
  background-color: #f8f9fa;
  border-radius: 8px;
  padding: 20px;
  margin: 15px 0;
}

.data-flow-steps {
  margin: 0;
  padding-left: 25px;
}

.data-flow-steps li {
  margin-bottom: 10px;
  position: relative;
}

.data-flow-steps li::marker {
  color: #66c0f4;
  font-weight: bold;
}

/* Api endpoints */
.endpoint-section {
  margin-bottom: 25px;
}

.endpoint-section h4 {
  color: #1b2838;
  margin-bottom: 15px;
}

.endpoint-list {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.endpoint-item {
  background-color: #f8f9fa;
  border-left: 4px solid #66c0f4;
  padding: 12px 15px;
  margin-bottom: 10px;
  border-radius: 0 4px 4px 0;
}

.endpoint-method {
  display: inline-block;
  padding: 3px 8px;
  background-color: #1b2838;
  color: #fff;
  border-radius: 4px;
  font-size: 0.8em;
  margin-right: 10px;
}

.endpoint-path {
  font-family: monospace;
  font-weight: bold;
  color: #333;
}

.endpoint-description {
  margin-top: 5px;
  color: #666;
  font-size: 0.9em;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .overview-tiers {
    flex-direction: column;
  }
  
  .definitions-table,
  .principles-grid,
  .api-modules-grid {
    grid-template-columns: 1fr;
  }
}
</style>

<div class="architecture-header">
  <h1>SteamGenie Architecture Document</h1>
  <div class="architecture-meta">
    <p><strong>Version:</strong> 1.0</p>
    <p><strong>Date:</strong> December 12, 2023</p>
    <p><strong>Authors:</strong> Yuxuan Ma, Team SteamGenie</p>
    <p><strong>Project:</strong> SteamGenie - AI-Powered Game Discovery Platform</p>
  </div>
</div>

<div class="toc-container">
  <h2>Table of Contents</h2>
  <ol class="toc-list">
    <li><a href="#introduction">Introduction</a></li>
    <li><a href="#system-overview">System Overview</a></li>
    <li><a href="#architecture-principles">Architecture Principles</a></li>
    <li><a href="#component-architecture">Component Architecture</a></li>
    <li><a href="#data-architecture">Data Architecture</a></li>
    <li><a href="#api-architecture">API Architecture</a></li>
    <li><a href="#ai-implementation">AI Implementation</a></li>
    <li><a href="#deployment-architecture">Deployment Architecture</a></li>
    <li><a href="#performance-considerations">Performance Considerations</a></li>
    <li><a href="#security-considerations">Security Considerations</a></li>
    <li><a href="#appendices">Appendices</a></li>
  </ol>
</div>

<div id="introduction" class="section">
  <h2>1. Introduction</h2>

  <div class="subsection">
    <h3>1.1 Purpose</h3>
    <p>This document provides a comprehensive overview of the architectural design of SteamGenie, an AI-powered game discovery platform. It serves as a reference for developers, stakeholders, and future contributors to understand the system's technical implementation, component interactions, and design decisions.</p>
  </div>

  <div class="subsection">
    <h3>1.2 Scope</h3>
    <p>This architecture document covers:</p>
    <ul class="scope-list">
      <li>System components and their interactions</li>
      <li>Data flow and storage designs</li>
      <li>API endpoints and specifications</li>
      <li>AI/ML implementation details</li>
      <li>Deployment strategy and infrastructure</li>
      <li>Performance optimization techniques</li>
      <li>Security measures</li>
    </ul>
  </div>

  <div class="subsection">
    <h3>1.3 Definitions, Acronyms, and Abbreviations</h3>
    <div class="definitions-table">
      <div class="definition-item">
        <div class="term">LLM</div>
        <div class="definition">Large Language Model</div>
      </div>
      <div class="definition-item">
        <div class="term">NLP</div>
        <div class="definition">Natural Language Processing</div>
      </div>
      <div class="definition-item">
        <div class="term">API</div>
        <div class="definition">Application Programming Interface</div>
      </div>
      <div class="definition-item">
        <div class="term">UI/UX</div>
        <div class="definition">User Interface/User Experience</div>
      </div>
      <div class="definition-item">
        <div class="term">MongoDB</div>
        <div class="definition">NoSQL database used for SteamGenie</div>
      </div>
      <div class="definition-item">
        <div class="term">React</div>
        <div class="definition">Frontend JavaScript library</div>
      </div>
      <div class="definition-item">
        <div class="term">Express</div>
        <div class="definition">Backend web application framework</div>
      </div>
      <div class="definition-item">
        <div class="term">ETL</div>
        <div class="definition">Extract, Transform, Load (data processing)</div>
      </div>
      <div class="definition-item">
        <div class="term">CDN</div>
        <div class="definition">Content Delivery Network</div>
      </div>
    </div>
  </div>
</div>

<div id="system-overview" class="section">
  <h2>2. System Overview</h2>

  <p>SteamGenie is a web-based application that helps users discover games through natural language interactions and advanced filtering. The system architecture follows a modern three-tier design with:</p>

  <div class="overview-tiers">
    <div class="tier-card">
      <h4>Frontend Tier</h4>
      <p>React.js single-page application with responsive design</p>
    </div>
    <div class="tier-card">
      <h4>API Tier</h4>
      <p>Express.js RESTful API layer</p>
    </div>
    <div class="tier-card">
      <h4>Data Tier</h4>
      <p>MongoDB database with optimized query patterns</p>
    </div>
  </div>

  <p>Additionally, the system integrates AI/ML components for natural language understanding and recommendation generation.</p>

  <div class="subsection">
    <h3>2.1 System Context Diagram</h3>
    <div class="context-diagram">
      <pre class="diagram">
┌───────────────────┐     HTTP Requests     ┌───────────────────┐
│                   │<────────────────────>│                   │
│      End User     │                      │    SteamGenie     │
│                   │<────────────────────>│     Frontend      │
└───────────────────┘     UI Responses     └────────┬──────────┘
                                                    │
                                                    │ API Calls
                                                    ▼
                          ┌───────────────────────────────────────┐
                          │                                       │
                          │           Express.js API              │
                          │                                       │
                          └─┬─────────────────┬─────────────────┬─┘
                            │                 │                 │
               ┌────────────▼─────┐ ┌─────────▼────────┐ ┌─────▼──────────┐
               │                  │ │                  │ │                │
               │  Game Database   │ │   AI Services    │ │  Steam API     │
               │    (MongoDB)     │ │  (NLP/Embeddings)│ │  Integration   │
               │                  │ │                  │ │                │
               └──────────────────┘ └──────────────────┘ └────────────────┘
      </pre>
    </div>
  </div>
</div>

<div id="architecture-principles" class="section">
  <h2>3. Architecture Principles</h2>

  <p>The SteamGenie architecture adheres to the following principles:</p>

  <div class="subsection">
    <h3>3.1 Design Principles</h3>
    <div class="principles-grid">
      <div class="principle-card">
        <h4>Separation of Concerns</h4>
        <p>Clearly defined boundaries between components</p>
      </div>
      <div class="principle-card">
        <h4>Single Responsibility</h4>
        <p>Each module has one reason to change</p>
      </div>
      <div class="principle-card">
        <h4>API-First Design</h4>
        <p>Well-defined APIs to enable modular development</p>
      </div>
      <div class="principle-card">
        <h4>Progressive Enhancement</h4>
        <p>Core functionality works without JavaScript</p>
      </div>
      <div class="principle-card">
        <h4>Responsive Design</h4>
        <p>Mobile-first approach to UI components</p>
      </div>
    </div>
  </div>

  <div class="subsection">
    <h3>3.2 Implementation Principles</h3>
    <div class="principles-grid">
      <div class="principle-card">
        <h4>Stateless Services</h4>
        <p>API servers maintain no client session state</p>
      </div>
      <div class="principle-card">
        <h4>Optimistic UI Updates</h4>
        <p>Frontend updates before backend confirmation</p>
      </div>
      <div class="principle-card">
        <h4>Immutable Data Flow</h4>
        <p>One-way data flow in UI components</p>
      </div>
      <div class="principle-card">
        <h4>Fail Fast</h4>
        <p>Early validation and error detection</p>
      </div>
      <div class="principle-card">
        <h4>Graceful Degradation</h4>
        <p>System remains functional during partial failures</p>
      </div>
    </div>
  </div>
</div>

<div id="component-architecture" class="section">
  <h2>4. Component Architecture</h2>

  <div class="subsection">
    <h3>4.1 Frontend Architecture</h3>
    <p>The frontend is built using React with a component-based architecture following atomic design principles.</p>

    <div class="component-section">
      <h4>4.1.1 Component Hierarchy</h4>
      <div class="code-block">
        <pre>
App
├── Header
│   ├── Logo
│   ├── SearchBar
│   └── NavigationMenu
├── GameDiscovery
│   ├── ConversationalInterface
│   │   ├── MessageHistory
│   │   └── InputArea
│   ├── FilterPanel
│   │   ├── PriceFilter
│   │   ├── GenreFilter
│   │   ├── TagFilter
│   │   └── ReleaseFilter
│   └── ResultsGrid
│       ├── GameCard
│       └── LoadMore
├── GameDetail
│   ├── GameHeader
│   ├── MediaGallery
│   ├── GameDescription
│   ├── GameMetadata
│   └── SimilarGames
└── Footer
        </pre>
      </div>
    </div>

    <div class="component-section">
      <h4>4.1.2 State Management</h4>
      <p>SteamGenie uses Redux for global state management with the following slices:</p>
      <ul class="feature-list">
        <li><span class="feature-highlight">User Preferences:</span> Stores filter settings and history</li>
        <li><span class="feature-highlight">Search Results:</span> Manages game data and pagination</li>
        <li><span class="feature-highlight">UI State:</span> Controls modals, loading states, etc.</li>
        <li><span class="feature-highlight">Conversation:</span> Maintains chat history with AI</li>
      </ul>
      <p>Context API is used for feature-specific state that doesn't need global persistence.</p>
    </div>
  </div>

  <div class="subsection">
    <h3>4.2 Backend Architecture</h3>
    <p>The backend follows a service-oriented architecture with clearly defined boundaries:</p>

    <div class="component-section">
      <h4>4.2.1 Service Layers</h4>
      <div class="code-block">
        <pre>
┌─────────────────────────────────────────────────┐
│              API Gateway Layer                  │
│  (Request Validation, Rate Limiting, Routing)   │
└───────────────┬─────────────────┬──────────────┘
                │                 │
    ┌───────────▼────────┐ ┌─────▼──────────────┐
    │                    │ │                    │
    │  Game Service      │ │  Query Service     │
    │  (Game CRUD)       │ │  (Search, Filter)  │
    │                    │ │                    │
    └────────┬───────────┘ └─────────┬──────────┘
             │                       │
    ┌────────▼───────────────────────▼──────────┐
    │                                           │
    │          Data Access Layer                │
    │  (MongoDB Repositories, Caching)          │
    │                                           │
    └───────────────────┬───────────────────────┘
                        │
                ┌───────▼────────┐
                │                │
                │   MongoDB      │
                │                │
                └────────────────┘
        </pre>
      </div>
    </div>

    <div class="component-section">
      <h4>4.2.2 API Modules</h4>
      <div class="api-modules-grid">
        <div class="api-module-card">
          <h5>Authentication</h5>
          <p>Handles user sessions and authentication (future)</p>
        </div>
        <div class="api-module-card">
          <h5>Games</h5>
          <p>CRUD operations for game data</p>
        </div>
        <div class="api-module-card">
          <h5>Search</h5>
          <p>Advanced search and filtering endpoints</p>
        </div>
        <div class="api-module-card">
          <h5>Recommendations</h5>
          <p>Game recommendation endpoints</p>
        </div>
        <div class="api-module-card">
          <h5>Conversation</h5>
          <p>NLP processing endpoints</p>
        </div>
      </div>
    </div>
  </div>
</div>

<div id="data-architecture" class="section">
  <h2>5. Data Architecture</h2>

  <div class="subsection">
    <h3>5.1 Database Schema</h3>
    <p>SteamGenie uses MongoDB with the following main collections:</p>

    <div class="schema-section">
      <h4>5.1.1 Games Collection</h4>
      <div class="code-block json">
        <pre>
{
  "_id": "ObjectId('5f8a7b6c9b2e7a1d2c3b4a5d')",
  "steamId": 1091500,
  "name": "Cyberpunk 2077",
  "description": "Cyberpunk 2077 is an open-world, action-adventure...",
  "shortDescription": "Night City changes every body...",
  "headerImage": "https://cdn.cloudflare.steamstatic.com/steam/apps/1091500/header.jpg",
  "publishers": ["CD PROJEKT RED"],
  "developers": ["CD PROJEKT RED"],
  "price": {
    "currency": "USD",
    "initial": 59.99,
    "final": 59.99,
    "discountPercent": 0
  },
  "genres": ["RPG", "Open World", "Action", "Cyberpunk"],
  "tags": [
    {"name": "Open World", "count": 12500},
    {"name": "Cyberpunk", "count": 10200},
    {"name": "RPG", "count": 9800},
    {"name": "Sci-fi", "count": 7600}
  ],
  "categories": ["Single-player", "Steam Achievements", "Steam Trading Cards"],
  "releaseDate": "2020-12-10T00:00:00Z",
  "reviewSummary": {
    "positive": 76,
    "total": 100,
    "sentiment": "Mostly Positive"
  },
  "screenshots": [
    "https://cdn.cloudflare.steamstatic.com/steam/apps/1091500/ss_1.jpg",
    "https://cdn.cloudflare.steamstatic.com/steam/apps/1091500/ss_2.jpg"
  ],
  "platforms": ["windows", "mac"],
  "metacritic": {
    "score": 86,
    "url": "https://www.metacritic.com/game/pc/cyberpunk-2077"
  },
  "embeddings": {
    "description": [0.123, -0.456, 0.789...],
    "tags": [0.321, -0.654, 0.987...]
  },
  "lastUpdated": "2023-11-20T10:15:22Z",
  "searchableText": "cyberpunk 2077 rpg open world action cd projekt red sci-fi..."
}
        </pre>
      </div>
    </div>

    <div class="schema-section">
      <h4>5.1.2 Queries Collection</h4>
      <div class="code-block json">
        <pre>
{
  "_id": "ObjectId('5f8a7b6c9b2e7a1d2c3b4a5e')",
  "text": "first person shooter with zombies and cooperative gameplay",
  "timestamp": "2023-11-20T10:17:42Z",
  "structuredQuery": {
    "genres": ["FPS"],
    "tags": ["Zombies", "Co-op"],
    "must": ["First-Person", "Multiplayer"],
    "should": ["Horror", "Survival"],
    "must_not": ["Early Access", "Visual Novel"]
  },
  "resultCount": 12,
  "clickedGames": [378, 12495],
  "anonymizedUserId": "a2c45fd9"
}
        </pre>
      </div>
    </div>
  </div>

  <div class="subsection">
    <h3>5.2 Data Flow</h3>
    <p>The data flow through the SteamGenie system follows this pattern:</p>
    
    <div class="data-flow-container">
      <ol class="data-flow-steps">
        <li>User submits a natural language query</li>
        <li>Query is processed by NLP service to extract structured parameters</li>
        <li>Structured query is used to fetch matching games from database</li>
        <li>Results are enriched with recommendation algorithms</li>
        <li>Ranked results are returned to the frontend</li>
        <li>User interactions with results are logged for refinement</li>
      </ol>
    </div>
  </div>
</div>

<div id="api-architecture" class="section">
  <h2>6. API Architecture</h2>

  <div class="subsection">
    <h3>6.1 API Endpoints</h3>
    <p>SteamGenie exposes the following RESTful API endpoints:</p>

    <div class="subsection">
      <h4>Games API</h4>
      <ul class="api-endpoints">
        <li>`GET /api/games` - List games with filtering</li>
        <li>`GET /api/games/:id` - Get detailed game information</li>
        <li>`GET /api/games/similar/:id` - Get similar games</li>
      </ul>
    </div>

    <div class="subsection">
      <h4>Search API</h4>
      <ul class="api-endpoints">
        <li>`POST /api/search` - Execute structured search query</li>
        <li>`GET /api/search/popular` - Get popular search queries</li>
        <li>`POST /api/search/nlp` - Process natural language query</li>
      </ul>
    </div>

    <div class="subsection">
      <h4>Recommendations API</h4>
      <ul class="api-endpoints">
        <li>`GET /api/recommendations` - Get personalized recommendations</li>
        <li>`POST /api/recommendations/feedback` - Submit feedback on recommendations</li>
      </ul>
    </div>
  </div>

  <div class="subsection">
    <h3>6.2 API Example Request</h3>
    <div class="api-example">
      <pre class="request">
POST /api/search/nlp
Content-Type: application/json

{
  "query": "story-driven RPGs with beautiful visuals like Witcher 3",
  "limit": 10,
  "filters": {
    "maxPrice": 60,
    "platforms": ["windows"]
  }
}
      </pre>
    </div>
  </div>

  <div class="subsection">
    <h3>6.3 API Example Response</h3>
    <div class="api-example">
      <pre class="response">
{
  "success": true,
  "results": {
    "games": [
      {
        "id": 292030,
        "name": "The Witcher 3: Wild Hunt",
        "headerImage": "https://cdn.cloudflare.steamstatic.com/steam/apps/292030/header.jpg",
        "price": {"final": 39.99, "currency": "USD"},
        "genres": ["RPG", "Open World", "Story Rich"],
        "relevanceScore": 0.98
      },
      {
        "id": 1091500,
        "name": "Cyberpunk 2077",
        "headerImage": "https://cdn.cloudflare.steamstatic.com/steam/apps/1091500/header.jpg",
        "price": {"final": 59.99, "currency": "USD"},
        "genres": ["RPG", "Open World", "Cyberpunk"],
        "relevanceScore": 0.92
      }
      // Additional results...
    ],
    "total": 128,
    "page": 1,
    "pageSize": 10
  },
  "query": {
    "original": "story-driven RPGs with beautiful visuals like Witcher 3",
    "interpreted": {
      "genres": ["RPG"],
      "attributes": ["Story Rich", "Beautiful", "Atmospheric"],
      "similar_to": [292030]
    },
    "suggestedRefinements": [
      "Add 'Open World' to see more exploration-focused games",
      "Filter by 'Fantasy' to focus on similar settings"
    ]
  }
}
      </pre>
    </div>
  </div>
</div>

<div id="ai-implementation" class="section">
  <h2>7. AI Implementation</h2>

  <div class="subsection">
    <h3>7.1 Natural Language Processing</h3>
    <p>SteamGenie implements NLP capabilities through:</p>
    <ul class="nlp-capabilities">
      <li>**Query Understanding**: Converting natural language to structured queries</li>
      <li>**Intent Classification**: Identifying search intent vs. conversation</li>
      <li>**Entity Extraction**: Identifying game titles, genres, mechanics</li>
      <li>**Sentiment Analysis**: Understanding subjective preferences</li>
    </ul>
  </div>

  <div class="subsection">
    <h3>7.2 Recommendation Engine</h3>
    <p>The recommendation system uses a hybrid approach combining:</p>
    <ul class="recommendation-engine">
      <li>**Content-Based Filtering**: Using game attributes and descriptions</li>
      <li>**Collaborative Filtering**: Using user preference patterns</li>
      <li>**Knowledge-Based Recommendations**: Using domain-specific rules</li>
      <li>**Vector Embeddings**: Using semantic similarity between games</li>
    </ul>
  </div>

  <div class="subsection">
    <h3>7.3 Vector Embedding Architecture</h3>
    <div class="embedding-architecture">
      <pre class="architecture">
┌─────────────────┐         ┌────────────────────┐
│                 │         │                    │
│  Game Metadata  │ ──────> │ Embedding Pipeline │
│                 │         │                    │
└─────────────────┘         └──────────┬─────────┘
                                       │
                                       ▼
                            ┌─────────────────────┐
                            │                     │
                            │  Vector Database    │
                            │                     │
                            └─────────┬───────────┘
                                      │
                                      │
┌─────────────────┐         ┌────────▼───────────┐
│                 │         │                    │
│  User Query     │ ──────> │ Similarity Search  │
│                 │         │                    │
└─────────────────┘         └────────────────────┘
      </pre>
    </div>
  </div>
</div>

<div id="deployment-architecture" class="section">
  <h2>8. Deployment Architecture</h2>

  <div class="subsection">
    <h3>8.1 Infrastructure</h3>
    <p>SteamGenie is deployed using a serverless architecture on Vercel with the following components:</p>
    <div class="infrastructure">
      <pre class="infrastructure">
┌───────────────────────────────────────────────────────────┐
│                     Vercel Platform                       │
│                                                           │
│  ┌─────────────────┐          ┌────────────────────────┐  │
│  │                 │          │                        │  │
│  │  React Frontend │◄────────►│  Serverless Functions  │  │
│  │  (Static Files) │          │  (Express.js API)      │  │
│  │                 │          │                        │  │
│  └─────────────────┘          └───────────┬────────────┘  │
│                                           │               │
└───────────────────────────────────────────│───────────────┘
                                            │
                                            ▼
                              ┌─────────────────────────────┐
                              │                             │
                              │    MongoDB Atlas Cloud      │
                              │                             │
                              └─────────────────────────────┘
      </pre>
    </div>
  </div>

  <div class="subsection">
    <h3>8.2 CI/CD Pipeline</h3>
    <p>The continuous integration and deployment workflow follows these steps:</p>
    <ol class="ci-cd-steps">
      <li>Code pushed to GitLab repository</li>
      <li>Automated tests run (Jest, React Testing Library)</li>
      <li>ESLint and type checking with TypeScript</li>
      <li>Build process generates optimized assets</li>
      <li>Deployment to staging environment</li>
      <li>Manual QA testing</li>
      <li>Promotion to production</li>
    </ol>
  </div>
</div>

<div id="performance-considerations" class="section">
  <h2>9. Performance Considerations</h2>

  <div class="subsection">
    <h3>9.1 Caching Strategy</h3>
    <p>SteamGenie implements a multi-tiered caching strategy:</p>
    <ul class="caching-strategy">
      <li>**Browser Cache**: Static assets with appropriate cache headers</li>
      <li>**CDN Cache**: Frontend assets cached at edge locations</li>
      <li>**API Cache**: Common queries cached with Redis</li>
      <li>**Database Cache**: Frequently accessed documents cached in memory</li>
    </ul>
  </div>

  <div class="subsection">
    <h3>9.2 Performance Optimizations</h3>
    <p>The following techniques are employed to ensure optimal performance:</p>
    <ul class="performance-optimizations">
      <li>**Code Splitting**: Dynamic loading of React components</li>
      <li>**Image Optimization**: WebP format with responsive sizes</li>
      <li>**Lazy Loading**: Images and components loaded as needed</li>
      <li>**Query Optimization**: MongoDB indexes for common query patterns</li>
      <li>**Debouncing**: Limiting API calls during user input</li>
      <li>**Connection Pooling**: Reusing database connections</li>
    </ul>
  </div>
</div>

<div id="security-considerations" class="section">
  <h2>10. Security Considerations</h2>

  <div class="subsection">
    <h3>10.1 Security Measures</h3>
    <p>SteamGenie implements the following security measures:</p>
    <ul class="security-measures">
      <li>**Input Validation**: All user inputs validated on client and server</li>
      <li>**Rate Limiting**: API endpoints protected against abuse</li>
      <li>**Content Security Policy**: Prevents XSS attacks</li>
      <li>**HTTPS Only**: All communications encrypted</li>
      <li>**API Key Rotation**: Regular rotation of third-party API keys</li>
      <li>**Dependency Scanning**: Regular checks for vulnerable dependencies</li>
    </ul>
  </div>

  <div class="subsection">
    <h3>10.2 Privacy Measures</h3>
    <p>User privacy is protected through:</p>
    <ul class="privacy-measures">
      <li>**Anonymized Analytics**: No personally identifiable information</li>
      <li>**Query Logging**: User queries stored without identifying information</li>
      <li>**Transparent Cookies**: Clear cookie usage disclosure</li>
      <li>**Data Minimization**: Only collecting necessary data</li>
    </ul>
  </div>
</div>

<div id="appendices" class="section">
  <h2>11. Appendices</h2>

  <div class="subsection">
    <h3>11.1 Technology Stack Summary</h3>
    <p>The following technologies are used in the SteamGenie project:</p>
    <ul class="technology-stack">
      <li>**Frontend**: React, TypeScript, Redux, Tailwind CSS</li>
      <li>**Backend**: Node.js, Express.js, MongoDB</li>
      <li>**AI/ML**: TensorFlow.js, custom NLP pipeline</li>
      <li>**DevOps**: Vercel, GitLab CI/CD, Jest</li>
      <li>**Monitoring**: Sentry, Vercel Analytics</li>
    </ul>
  </div>

  <div class="subsection">
    <h3>11.2 External Dependencies</h3>
    <p>The following external dependencies are used:</p>
    <ul class="external-dependencies">
      <li>**Steam API**</li>
      <li>**MongoDB Atlas**</li>
      <li>**Vercel Edge Functions**</li>
      <li>**OpenAI API (for NLP processing)**</li>
    </ul>
  </div>

  <div class="subsection">
    <h3>11.3 Environment Variables</h3>
    <p>The following environment variables are used in the project:</p>
    <div class="environment-variables">
      <pre class="variables">
# API Configuration
API_BASE_URL=https://api.steamgenie.vercel.app
API_VERSION=v1
API_TIMEOUT=5000

# Database Connection
MONGODB_URI=mongodb+srv://[username]:[password]@cluster0.mongodb.net/steamgenie
MONGODB_DB_NAME=steamgenie

# External APIs
STEAM_API_KEY=[redacted]
OPENAI_API_KEY=[redacted]

# Performance
CACHE_TTL=3600
MAX_QUERY_RESULTS=100

# Security
CORS_ALLOWED_ORIGINS=https://steamgenie.vercel.app,http://localhost:3000
      </pre>
    </div>
  </div>
</div>

---

Document Revision History:
- v1.0 (2023-12-12): Initial architecture document
- v0.2 (2023-11-15): Draft review with team feedback
- v0.1 (2023-10-28): Initial draft 