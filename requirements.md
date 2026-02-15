# Requirements Document

## Introduction

Tark 2.0 (The Logic Engine) is an AI-powered educational platform that teaches reasoning by refusing to provide answers until users demonstrate logical thinking. The system evaluates user logic with partial credit scoring, identifies hidden assumptions, and provides contextual learning resources across coding, finance, and hardware domains.

## Glossary

- **Logic_Engine**: The core AI system that evaluates and scores user reasoning
- **Guided_Nudge**: Contextual hints provided when user logic is partially correct (1-99% score)
- **Assumption_Detector**: Component that identifies unstated assumptions in user reasoning
- **Logic_Memory**: Session-based system that tracks and adapts to user thinking patterns
- **Resource_Ranker**: Component that fetches and ranks external learning resources by difficulty and relevance
- **Expert_Logic**: Reference reasoning provided by domain experts for comparison
- **Logic_Score**: Numerical assessment (0-100%) of user reasoning quality
- **Session**: A continuous interaction period where Logic_Memory accumulates user patterns

## Requirements

### Requirement 1: Logic Evaluation and Scoring

**User Story:** As a learner, I want my reasoning to be evaluated with partial credit, so that I can understand what parts of my logic are correct and what needs improvement.

#### Acceptance Criteria

1. WHEN a user submits reasoning for a problem, THE Logic_Engine SHALL evaluate it and assign a Logic_Score between 0-100%
2. WHEN the Logic_Score is 0%, THE Logic_Engine SHALL provide clear feedback on fundamental logical errors
3. WHEN the Logic_Score is between 1-99%, THE Logic_Engine SHALL generate Guided_Nudges highlighting correct elements and areas for improvement
4. WHEN the Logic_Score is 100%, THE Logic_Engine SHALL unlock the complete solution and Expert_Logic comparison
5. THE Logic_Engine SHALL evaluate reasoning based on logical structure, completeness, and domain-specific accuracy

### Requirement 2: Guided Nudge System

**User Story:** As a learner, I want contextual hints when my logic is partially correct, so that I can improve my reasoning without getting the full answer immediately.

#### Acceptance Criteria

1. WHEN a user receives a Logic_Score between 1-99%, THE Logic_Engine SHALL generate specific Guided_Nudges
2. WHEN providing Guided_Nudges, THE Logic_Engine SHALL highlight which parts of the user's reasoning are correct
3. WHEN providing Guided_Nudges, THE Logic_Engine SHALL identify specific gaps or errors without revealing the complete solution
4. THE Guided_Nudges SHALL be tailored to the user's current Logic_Score range (different hints for 20% vs 80%)
5. THE Logic_Engine SHALL limit Guided_Nudges to preserve the learning challenge while providing meaningful direction

### Requirement 3: Assumption Detection

**User Story:** As a learner, I want the system to identify hidden assumptions in my reasoning, so that I can develop more rigorous logical thinking.

#### Acceptance Criteria

1. WHEN evaluating user reasoning, THE Assumption_Detector SHALL identify unstated assumptions
2. WHEN assumptions are detected, THE Assumption_Detector SHALL explicitly state what the user assumed
3. WHEN assumptions are identified, THE Assumption_Detector SHALL explain why the assumption may be invalid or limiting
4. THE Assumption_Detector SHALL distinguish between reasonable implicit assumptions and problematic unstated assumptions
5. WHEN no assumptions are detected, THE Assumption_Detector SHALL confirm that the reasoning appears assumption-free

### Requirement 4: Logic Memory and Adaptation

**User Story:** As a learner, I want the system to remember my thinking patterns during a session, so that it can provide personalized feedback based on my recurring logical tendencies.

#### Acceptance Criteria

1. WHEN a user starts a new Session, THE Logic_Memory SHALL initialize an empty pattern tracking system
2. WHEN a user submits reasoning, THE Logic_Memory SHALL analyze and store patterns in their logical approach
3. WHEN patterns are identified, THE Logic_Memory SHALL adapt feedback to address the user's specific thinking tendencies
4. WHEN a Session ends, THE Logic_Memory SHALL reset and not persist data across sessions
5. THE Logic_Memory SHALL identify common patterns such as edge case oversight, assumption-heavy reasoning, or incomplete analysis

### Requirement 5: Expert Logic Comparison

**User Story:** As a learner, I want to compare my reasoning with expert logic, so that I can understand different approaches and improve my thinking.

#### Acceptance Criteria

1. WHEN a user achieves a 100% Logic_Score, THE Logic_Engine SHALL display a side-by-side comparison of User's Logic vs Expert_Logic
2. WHEN displaying Expert_Logic, THE Logic_Engine SHALL highlight key differences in approach and reasoning structure
3. WHEN showing comparisons, THE Logic_Engine SHALL explain why the Expert_Logic approach is effective
4. THE Expert_Logic SHALL be domain-appropriate and represent best practices for the specific problem type
5. THE comparison view SHALL clearly distinguish between user reasoning and expert reasoning sections

### Requirement 6: Contextual Resource Ranking

**User Story:** As a learner, I want access to ranked learning resources when I unlock solutions, so that I can deepen my understanding with appropriate difficulty-level materials.

#### Acceptance Criteria

1. WHEN a user unlocks a solution (100% Logic_Score), THE Resource_Ranker SHALL fetch relevant YouTube and Reddit resources
2. WHEN displaying resources, THE Resource_Ranker SHALL rank them by difficulty level (Beginner/Advanced)
3. WHEN displaying resources, THE Resource_Ranker SHALL rank them by relevance to the specific problem domain
4. THE Resource_Ranker SHALL integrate with YouTube Data API to fetch video content
5. THE Resource_Ranker SHALL provide clear difficulty and relevance indicators for each resource

### Requirement 7: Multi-Domain Problem Support

**User Story:** As a learner, I want to practice logical reasoning across different domains, so that I can develop versatile thinking skills.

#### Acceptance Criteria

1. THE Logic_Engine SHALL support coding domain problems with programming logic evaluation
2. THE Logic_Engine SHALL support finance domain problems with financial reasoning evaluation
3. THE Logic_Engine SHALL support hardware domain problems with technical system reasoning evaluation
4. WHEN switching domains, THE Logic_Engine SHALL adapt evaluation criteria to domain-specific logical requirements
5. THE Logic_Engine SHALL maintain consistent scoring methodology across all supported domains

### Requirement 8: User Interface and Experience

**User Story:** As a learner, I want an intuitive interface for submitting reasoning and viewing feedback, so that I can focus on learning rather than navigating the system.

#### Acceptance Criteria

1. THE User_Interface SHALL provide a clear text input area for reasoning submission
2. WHEN displaying Logic_Scores, THE User_Interface SHALL show the percentage prominently with visual indicators
3. WHEN showing Guided_Nudges, THE User_Interface SHALL distinguish them visually from other feedback types
4. WHEN displaying Expert_Logic comparisons, THE User_Interface SHALL use a clear side-by-side layout
5. THE User_Interface SHALL provide easy navigation between different problem domains

### Requirement 9: External API Integration

**User Story:** As a system administrator, I want reliable integration with external APIs, so that the platform can fetch resources and leverage AI capabilities effectively.

#### Acceptance Criteria

1. THE Logic_Engine SHALL integrate with Google Gemini 1.5 Pro API for reasoning evaluation
2. THE Resource_Ranker SHALL integrate with YouTube Data API for video resource fetching
3. WHEN API calls fail, THE Logic_Engine SHALL provide graceful error handling and fallback responses
4. THE Logic_Engine SHALL implement appropriate rate limiting for external API usage
5. THE Logic_Engine SHALL validate API responses before processing and displaying content

### Requirement 10: Session Management

**User Story:** As a learner, I want my learning session to be tracked consistently, so that the system can adapt to my thinking patterns during my practice time.

#### Acceptance Criteria

1. WHEN a user starts using the platform, THE Logic_Engine SHALL initialize a new Session
2. WHEN a Session is active, THE Logic_Memory SHALL continuously track and analyze user reasoning patterns
3. WHEN a user closes the application or is inactive, THE Logic_Engine SHALL end the current Session
4. WHEN a Session ends, THE Logic_Memory SHALL clear all stored patterns and reset adaptation
5. THE Logic_Engine SHALL maintain Session state consistently throughout the user's active learning period