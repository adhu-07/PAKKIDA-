# Pakkida - The Ghostly Board Game

## Overview

Pakkida is a web-based board game inspired by the movie "Padakkalam" and classic Pachisi. It's a mystical, ancient-themed game where 2-3 players control animal pieces (Lion, Horse, Elephant) on an 11x11 cross-shaped board. The game features AI integration through Google's Gemini API, where an AI character named Raghavan (a ghost) influences gameplay through "cuts" and curses.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS with custom ancient/mystical theming
- **UI Components**: Radix UI primitives with shadcn/ui components
- **State Management**: React hooks with custom game state management
- **Data Fetching**: TanStack Query (React Query) for API interactions
- **Routing**: Wouter for client-side routing
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Storage**: Configurable storage layer (currently in-memory for development)
- **API Design**: RESTful endpoints for game operations
- **Session Management**: Basic session handling for game state

### Key Components

#### Game Logic
- **Board**: 11x11 grid with cross-shaped path pattern
- **Pieces**: Three animal types (Lion 🦁, Horse 🐎, Elephant 🐘)
- **Dice**: Two 4-sided dice system
- **Movement Rules**: Players start in "nest" and can only exit with 1 or 4 roll
- **Winning Condition**: First player to reach center position (60) wins

#### AI Integration
- **Service**: Google Gemini 2.0 Flash model integration
- **Triggers**: AI responds to "cut" events and applies random curses
- **Functionality**: Generates mischievous instructions for affected players
- **Curse System**: Silent curse that affects players for 5 turns, activated after turn 10 with 5% chance

#### UI Components
- **GameBoard**: 11x11 grid visualization with path highlighting
- **PlayerCard**: Player status display with curse indicators
- **DiceControls**: Dice rolling interface with animations
- **RaghavanMessages**: AI message display component

## Data Flow

1. **Game Creation**: Players select pieces and start game
2. **Turn Management**: Sequential player turns with dice rolling
3. **Movement**: Piece movement with validation and animation
4. **Cut Events**: When pieces land on occupied spaces, trigger AI response
5. **Curse Application**: Random curse activation affects player movement
6. **State Persistence**: Game state stored in database with real-time updates

## External Dependencies

### Production Dependencies
- **AI Service**: Google Gemini API (`@google/genai`)
- **Database**: Neon PostgreSQL (`@neondatabase/serverless`)
- **ORM**: Drizzle ORM with Zod validation
- **UI Framework**: Radix UI components
- **State Management**: TanStack Query for server state
- **Styling**: Tailwind CSS with custom ancient theme

### Development Dependencies
- **Build System**: Vite with React plugin
- **TypeScript**: Full type safety across frontend and backend
- **Database Tools**: Drizzle Kit for schema management
- **Development Tools**: Replit-specific plugins for development environment

## Deployment Strategy

### Development Environment
- **Local Server**: Express server with Vite middleware
- **Hot Reload**: Vite HMR for React components
- **Database**: PostgreSQL connection via environment variables
- **AI Integration**: Gemini API key via environment variables

### Production Build
- **Frontend**: Vite build outputs to `dist/public`
- **Backend**: ESBuild bundles server to `dist/index.js`
- **Database**: Drizzle migrations applied via `db:push` command
- **Environment**: Production configuration with optimized builds

### Configuration Management
- **Environment Variables**: Database URL, Gemini API key
- **Build Scripts**: Separate development and production commands
- **Database Schema**: Shared schema definitions in `/shared` directory
- **Static Assets**: Vite handles asset optimization and bundling

The architecture supports a full-stack TypeScript application with real-time game state management, AI-driven gameplay elements, and a responsive ancient-themed UI suitable for both desktop and mobile play.

## Recent Changes (January 2025)

### User Preferences Update
- **Curse System**: Made curse system subtle and secretive - players don't know when they're cursed
- **Curse Timing**: Curse activation delayed to after turn 10 with reduced 5% probability
- **UI Changes**: Removed curse indicators from player cards and dice controls
- **Game Balance**: Increased curse duration to 5 turns for better game balance

### Technical Improvements
- Fixed TypeScript errors in storage layer with proper type handling
- Added game ID tracking for proper Raghavan message integration
- Improved dice roll validation and movement logic
- Enhanced error handling for API calls
- Removed loading screen issues during dice rolls