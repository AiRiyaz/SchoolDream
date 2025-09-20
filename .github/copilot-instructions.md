# SchoolDream AI Agent Instructions

## Project Overview
SchoolDream is a next-generation intelligent school management platform that goes beyond traditional administrative tools by incorporating AI-driven personalized learning, predictive analytics, and comprehensive stakeholder engagement. The platform serves students, teachers, parents, and administrators with innovative features that actively improve learning outcomes.

## Architecture & Technology Stack

### Core Technologies
- **Backend**: Node.js with TypeScript, Express.js framework
- **Frontend**: React Native (mobile) + React.js (web)
- **Database**: PostgreSQL (primary), Redis (caching), MongoDB (documents)
- **Cloud**: Microsoft Azure with AI/ML services
- **AI/ML**: Azure Cognitive Services, TensorFlow.js, OpenAI API integration

### Key Architectural Patterns
- **Microservices**: Core Module Service, AI/ML Engine Service, Integration Service
- **API-First**: All functionality exposed through RESTful APIs with Azure API Gateway
- **Event-Driven**: Real-time updates using Socket.io for live communications
- **Container-Based**: Kubernetes orchestration for scalability

## Core Innovative Features

### 1. AI Learning Companion (ALC)
```typescript
// Example: AI tutor integration pattern
interface LearningCompanion {
  analyzePerformance(studentId: string, subject: string): Promise<LearningInsight>;
  generatePersonalizedContent(learningStyle: LearningStyle): Promise<Content>;
  provideTutoring(question: string, context: StudentContext): Promise<TutoringResponse>;
}
```

### 2. Predictive Academic Wellness System (PAWS)
- Early warning algorithms for academic/emotional distress
- Mental health tracking through behavior pattern analysis
- Intervention recommendation engine

### 3. Dynamic Parent Engagement Analytics (DPEA)
- Parent engagement scoring and optimization
- Automated communication personalization
- Family learning environment assessment

## Development Conventions

### Code Organization
```
src/
├── services/           # Core business logic microservices
│   ├── core-module/   # Student/teacher/admin management
│   ├── ai-engine/     # ML models and AI processing
│   └── integration/   # Third-party API integrations
├── shared/            # Common utilities and types
├── mobile/            # React Native mobile app
└── web/              # React.js web portal
```

### AI/ML Integration Patterns
- All AI services implement `IAIService` interface for consistency
- ML models are versioned and A/B tested before deployment
- Real-time AI responses must complete within 2 seconds
- Fallback mechanisms for AI service unavailability

### Data Privacy & Security
- FERPA, COPPA, and GDPR compliance is mandatory
- All student data must be encrypted at rest and in transit
- Role-based access control (RBAC) for all user interactions
- Regular security audits and penetration testing

## Key Business Objectives
- **Academic Performance**: 25% improvement through personalized learning
- **Student Retention**: 40% reduction in dropout rates via early intervention
- **Parent Engagement**: 60% increase in meaningful parent participation
- **Operational Efficiency**: AI-driven resource optimization

## Critical Workflows

### Student Performance Analysis
1. Data collection from learning activities
2. AI pattern recognition and analysis
3. Predictive modeling for intervention needs
4. Automated alert generation for stakeholders
5. Personalized recommendation delivery

### AI Model Training Pipeline
1. Data preprocessing and anonymization
2. Feature engineering for educational contexts
3. Model training with cross-validation
4. A/B testing in controlled environments
5. Gradual rollout with performance monitoring

## Integration Points
- **LMS Integration**: Canvas, Moodle, Google Classroom APIs
- **Communication**: Microsoft Teams, Zoom SDK integration
- **Payment Processing**: Stripe, PayPal for fee management
- **Analytics**: Custom dashboard with Azure Analytics integration

## Development Guidelines
- Follow TypeScript strict mode for type safety
- Implement comprehensive error handling with structured logging
- Use Azure Key Vault for sensitive configuration management
- Maintain 90%+ test coverage for critical AI/ML components
- Document all API endpoints with OpenAPI specifications

## Deployment & Scaling
- Container-based deployment with Azure Kubernetes Service
- Auto-scaling policies based on user load and AI processing demands
- Blue-green deployment strategy for zero-downtime updates
- Multi-region deployment for global accessibility

## Monitoring & Analytics
- Real-time performance monitoring with Azure Application Insights
- AI model drift detection and retraining triggers
- User engagement analytics and A/B testing frameworks
- Educational outcome tracking and reporting dashboards