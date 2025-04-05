# SteamGenie Architecture Document

**Version:** 1.0  
**Date:** December 12, 2023  
**Authors:** Yuxuan Ma, Team SteamGenie  
**Project:** SteamGenie - AI-Powered Game Discovery Platform

## Table of Contents

1. [Introduction](#introduction)
2. [System Overview](#system-overview)
3. [Architecture Principles](#architecture-principles)
4. [Component Architecture](#component-architecture)
5. [Data Architecture](#data-architecture)
6. [API Architecture](#api-architecture)
7. [AI Implementation](#ai-implementation)
8. [Deployment Architecture](#deployment-architecture)
9. [Performance Considerations](#performance-considerations)
10. [Security Considerations](#security-considerations)
11. [Appendices](#appendices)

## 1. Introduction

### 1.1 Purpose

This document provides a comprehensive overview of the architectural design of SteamGenie, an AI-powered game discovery platform. It serves as a reference for developers, stakeholders, and future contributors to understand the system's technical implementation, component interactions, and design decisions.

### 1.2 Scope

This architecture document covers:
- System components and their interactions
- Data flow and storage designs
- API endpoints and specifications
- AI/ML implementation details
- Deployment strategy and infrastructure
- Performance optimization techniques
- Security measures

### 1.3 Definitions, Acronyms, and Abbreviations

- **LLM**: Large Language Model
- **NLP**: Natural Language Processing
- **API**: Application Programming Interface
- **UI/UX**: User Interface/User Experience
- **MongoDB**: NoSQL database used for SteamGenie
- **React**: Frontend JavaScript library
- **Express**: Backend web application framework
- **ETL**: Extract, Transform, Load (data processing)
- **CDN**: Content Delivery Network

## 2. System Overview

SteamGenie is a web-based application that helps users discover games through natural language interactions and advanced filtering. The system architecture follows a modern three-tier design with:

1. **Frontend Tier**: React.js single-page application with responsive design
2. **API Tier**: Express.js RESTful API layer
3. **Data Tier**: MongoDB database with optimized query patterns

Additionally, the system integrates AI/ML components for natural language understanding and recommendation generation.

### 2.1 System Context Diagram

```
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
```

## 3. Architecture Principles

The SteamGenie architecture adheres to the following principles:

### 3.1 Design Principles
- **Separation of Concerns**: Clearly defined boundaries between components
- **Single Responsibility**: Each module has one reason to change
- **API-First Design**: Well-defined APIs to enable modular development
- **Progressive Enhancement**: Core functionality works without JavaScript
- **Responsive Design**: Mobile-first approach to UI components

### 3.2 Implementation Principles
- **Stateless Services**: API servers maintain no client session state
- **Optimistic UI Updates**: Frontend updates before backend confirmation
- **Immutable Data Flow**: One-way data flow in UI components
- **Fail Fast**: Early validation and error detection
- **Graceful Degradation**: System remains functional during partial failures

## 4. Component Architecture

### 4.1 Frontend Architecture

The frontend is built using React with a component-based architecture following atomic design principles.

#### 4.1.1 Component Hierarchy

```
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
```

#### 4.1.2 State Management

SteamGenie uses Redux for global state management with the following slices:

- **User Preferences**: Stores filter settings and history
- **Search Results**: Manages game data and pagination
- **UI State**: Controls modals, loading states, etc.
- **Conversation**: Maintains chat history with AI

Context API is used for feature-specific state that doesn't need global persistence.

### 4.2 Backend Architecture

The backend follows a service-oriented architecture with clearly defined boundaries:

#### 4.2.1 Service Layers

```
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
```

#### 4.2.2 API Modules

- **Authentication**: Handles user sessions and authentication (future)
- **Games**: CRUD operations for game data
- **Search**: Advanced search and filtering endpoints
- **Recommendations**: Game recommendation endpoints
- **Conversation**: NLP processing endpoints

## 5. Data Architecture

### 5.1 Database Schema

SteamGenie uses MongoDB with the following main collections:

#### 5.1.1 Games Collection
```json
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
```

#### 5.1.2 Queries Collection
```json
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
```

### 5.2 Data Flow

The data flow through the SteamGenie system follows this pattern:

1. User submits a natural language query
2. Query is processed by NLP service to extract structured parameters
3. Structured query is used to fetch matching games from database
4. Results are enriched with recommendation algorithms
5. Ranked results are returned to the frontend
6. User interactions with results are logged for refinement

## 6. API Architecture

### 6.1 API Endpoints

SteamGenie exposes the following RESTful API endpoints:

#### Games API
- `GET /api/games` - List games with filtering
- `GET /api/games/:id` - Get detailed game information
- `GET /api/games/similar/:id` - Get similar games

#### Search API
- `POST /api/search` - Execute structured search query
- `GET /api/search/popular` - Get popular search queries
- `POST /api/search/nlp` - Process natural language query

#### Recommendations API
- `GET /api/recommendations` - Get personalized recommendations
- `POST /api/recommendations/feedback` - Submit feedback on recommendations

### 6.2 API Example Request

```http
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
```

### 6.3 API Example Response

```json
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
```

## 7. AI Implementation

### 7.1 Natural Language Processing

SteamGenie implements NLP capabilities through:

1. **Query Understanding**: Converting natural language to structured queries
2. **Intent Classification**: Identifying search intent vs. conversation
3. **Entity Extraction**: Identifying game titles, genres, mechanics
4. **Sentiment Analysis**: Understanding subjective preferences

### 7.2 Recommendation Engine

The recommendation system uses a hybrid approach combining:

1. **Content-Based Filtering**: Using game attributes and descriptions
2. **Collaborative Filtering**: Using user preference patterns
3. **Knowledge-Based Recommendations**: Using domain-specific rules
4. **Vector Embeddings**: Using semantic similarity between games

### 7.3 Vector Embedding Architecture

```
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
```

## 8. Deployment Architecture

### 8.1 Infrastructure

SteamGenie is deployed using a serverless architecture on Vercel with the following components:

```
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
```

### 8.2 CI/CD Pipeline

The continuous integration and deployment workflow follows these steps:

1. Code pushed to GitLab repository
2. Automated tests run (Jest, React Testing Library)
3. ESLint and type checking with TypeScript
4. Build process generates optimized assets
5. Deployment to staging environment
6. Manual QA testing
7. Promotion to production

## 9. Performance Considerations

### 9.1 Caching Strategy

SteamGenie implements a multi-tiered caching strategy:

1. **Browser Cache**: Static assets with appropriate cache headers
2. **CDN Cache**: Frontend assets cached at edge locations
3. **API Cache**: Common queries cached with Redis
4. **Database Cache**: Frequently accessed documents cached in memory

### 9.2 Performance Optimizations

The following techniques are employed to ensure optimal performance:

1. **Code Splitting**: Dynamic loading of React components
2. **Image Optimization**: WebP format with responsive sizes
3. **Lazy Loading**: Images and components loaded as needed
4. **Query Optimization**: MongoDB indexes for common query patterns
5. **Debouncing**: Limiting API calls during user input
6. **Connection Pooling**: Reusing database connections

## 10. Security Considerations

### 10.1 Security Measures

SteamGenie implements the following security measures:

1. **Input Validation**: All user inputs validated on client and server
2. **Rate Limiting**: API endpoints protected against abuse
3. **Content Security Policy**: Prevents XSS attacks
4. **HTTPS Only**: All communications encrypted
5. **API Key Rotation**: Regular rotation of third-party API keys
6. **Dependency Scanning**: Regular checks for vulnerable dependencies

### 10.2 Privacy Measures

User privacy is protected through:

1. **Anonymized Analytics**: No personally identifiable information
2. **Query Logging**: User queries stored without identifying information
3. **Transparent Cookies**: Clear cookie usage disclosure
4. **Data Minimization**: Only collecting necessary data

## 11. Appendices

### 11.1 Technology Stack Summary

- **Frontend**: React, TypeScript, Redux, Tailwind CSS
- **Backend**: Node.js, Express.js, MongoDB
- **AI/ML**: TensorFlow.js, custom NLP pipeline
- **DevOps**: Vercel, GitLab CI/CD, Jest
- **Monitoring**: Sentry, Vercel Analytics

### 11.2 External Dependencies

- Steam API
- MongoDB Atlas
- Vercel Edge Functions
- OpenAI API (for NLP processing)

### 11.3 Environment Variables

```
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
```

---

Document Revision History:
- v1.0 (2023-12-12): Initial architecture document
- v0.2 (2023-11-15): Draft review with team feedback
- v0.1 (2023-10-28): Initial draft 