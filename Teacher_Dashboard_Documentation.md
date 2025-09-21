# SchoolDream Teacher Dashboard Feature Documentation

## Overview

The Teacher Dashboard serves as the primary workspace for educators in the SchoolDream platform, providing a personalized, real-time interface for managing classroom activities, monitoring student performance, and accessing essential teaching tools. It aggregates data from across the platform to enable efficient lesson planning, proactive student support, and streamlined communication with stakeholders.

### Purpose
- **Primary Goal**: Deliver actionable insights through personalized widgets, enable rapid access to teaching functions, and facilitate data-driven instructional decisions.
- **Key Objectives**: Monitor class performance in real-time, manage daily lesson plans, track student progress, provide quick access to communication tools, and support professional development.
- **Scope**: Real-time data visualization, customizable widget layouts, integration with all teacher module components, and responsive design for various devices.

### Target Users
- **Classroom Teachers**: Primary users managing daily teaching activities and student interactions.
- **Substitute Teachers**: Access to lesson plans and class information for coverage periods.
- **Department Heads**: Oversight of multiple classes and teacher performance metrics.
- **Special Education Teachers**: Monitoring individualized education plans and accommodations.

### Integration with SchoolDream Platform
- **Data Sources**: Pulls from Academic Management (grades, attendance), User Management (student profiles), Communication Hub (messages), and other modules via Supabase real-time subscriptions.
- **Navigation Hub**: Provides shortcuts to all 10 core teacher components.
- **Real-time Updates**: Live synchronization of class data, student submissions, and notifications.
- **Analytics Integration**: Feeds into Reports & Analytics for detailed performance insights.

## Features

### Detailed Breakdown of Functionalities

1. **Personal Overview and Quick Stats**
   - **Description**: Personalized dashboard widgets displaying key performance indicators and quick statistics relevant to the teacher's daily activities and long-term goals.
   - **Sub-features**: Customizable KPI cards with attendance rates, assignment completion percentages, upcoming deadlines, student engagement metrics, and professional development progress; real-time data updates via Supabase subscriptions; trend indicators with visual charts; drill-down capabilities to detailed student views.
   - **Use Cases**: Daily check-in to assess class health, identifying students needing attention, tracking teaching effectiveness, preparing for parent-teacher conferences.
   - **Workflow**: Dashboard loads → Fetches teacher-specific KPIs → Renders personalized widgets → Updates in real-time → Teacher interacts with widgets for deeper insights.
   - **Integration**: Pulls data from Academic Management for grades/attendance, integrates with Student Progress Tracking for detailed analytics, connects with Communication Hub for notification counts.

2. **Class Performance Summaries**
   - **Description**: Comprehensive overviews of individual class performance with aggregated student data, learning objective mastery, and comparative analytics.
   - **Sub-features**: Class-wise grade distributions, attendance trends, assignment submission rates, learning objective progress tracking, comparative performance against school averages, student risk indicators, export capabilities for reports.
   - **Use Cases**: Identifying struggling classes or subjects, adjusting teaching strategies, preparing for departmental meetings, celebrating class achievements.
   - **Workflow**: System aggregates student data by class → Calculates performance metrics → Displays in summary widgets → Teacher reviews and takes action.
   - **Integration**: Sources data from Academic Management and Student Progress Tracking, feeds into Reports & Analytics for advanced breakdowns.

3. **Today's Lessons and Activities**
   - **Description**: Dynamic display of scheduled lessons, activities, and classroom events for the current day with quick access to materials and student lists.
   - **Sub-features**: Daily schedule view with lesson details, activity checklists, student attendance rosters, quick links to lesson plans and resources, time-based notifications, substitution notes for covering teachers.
   - **Use Cases**: Preparing for class transitions, ensuring all materials are ready, tracking activity completion, managing substitute teacher handovers.
   - **Workflow**: System fetches daily schedule from Lesson Planning → Displays in timeline format → Teacher accesses materials → Marks activities complete.
   - **Integration**: Syncs with Lesson Planning module for schedule data, integrates with Resources & Materials for quick access, connects with Classroom Management for attendance.

4. **Quick Action Buttons**
   - **Description**: One-click access to frequently performed teaching tasks and navigation to key functions within the teacher module.
   - **Sub-features**: Customizable action bar with common tasks (take attendance, create assignment, send message), keyboard shortcuts support, frequently used module access, quick student search, emergency alert buttons, action analytics for usage optimization.
   - **Use Cases**: Rapid response to classroom situations, efficient task completion during limited prep time, quick communication with parents or administrators.
   - **Workflow**: Teacher identifies common tasks → Adds to quick actions → Clicks button → Executes function or navigates directly.
   - **Integration**: Links to all teacher module components, integrates with user preferences for personalization.

5. **Professional Development Notifications**
   - **Description**: Intelligent notification system for professional development opportunities, deadlines, and completion tracking with personalized recommendations.
   - **Sub-features**: Upcoming PD session alerts, course enrollment reminders, certification renewal notices, personalized PD recommendations based on teaching focus, completion tracking with certificates, integration with external learning platforms.
   - **Use Cases**: Staying current with educational trends, meeting certification requirements, exploring new teaching methodologies, tracking professional growth.
   - **Workflow**: System monitors PD data → Generates personalized notifications → Displays in dashboard → Teacher engages with opportunities.
   - **Integration**: Connects with Professional Development module, integrates with Communication Hub for notifications, syncs with external PD providers.

6. **Dark/Light Mode Toggle**
   - **Description**: Seamless theme switching capability allowing teachers to customize the dashboard appearance for different environments and preferences.
   - **Sub-features**: Instant theme switching with smooth transitions, automatic system preference detection, custom color schemes, accessibility-focused high contrast options, theme persistence across sessions.
   - **Use Cases**: Reducing eye strain during evening planning, accommodating visual preferences, improving readability in various lighting conditions.
   - **Workflow**: Teacher clicks toggle → System applies theme → Persists preference → Applies to all dashboard elements.
   - **Integration**: Stored in user preferences, affects all teacher module interfaces.

7. **Customizable Widget Layout**
   - **Description**: Flexible dashboard layout system allowing teachers to arrange, resize, and configure widgets according to their workflow preferences.
   - **Sub-features**: Drag-and-drop widget positioning, resizable widgets with grid snapping, widget visibility controls, layout presets for different teaching scenarios, auto-save of custom layouts, responsive layout adaptation.
   - **Use Cases**: Optimizing workspace for different teaching tasks, accommodating various screen sizes, creating focused views for specific activities.
   - **Workflow**: Teacher drags widgets → Arranges layout → Saves configuration → Layout loads on login.
   - **Integration**: Layout data stored in user preferences, integrates with all dashboard widgets.

## Requirements

### Functional Requirements
- **Personal Overview**: Display personalized KPIs with real-time updates.
- **Class Summaries**: Show aggregated class performance data.
- **Daily Schedule**: Display today's lessons and activities.
- **Quick Actions**: Provide one-click access to common teaching tasks.
- **PD Notifications**: Display professional development alerts.
- **Theme Toggle**: Allow instant dark/light mode switching.
- **Widget Customization**: Enable drag-and-drop widget arrangement.
- **Real-time Updates**: Ensure live data synchronization.
- **Responsive Design**: Support mobile, tablet, and desktop layouts.

### Non-Functional Requirements
- **Performance**: Dashboard loads in < 2 seconds; real-time updates with < 1 second latency.
- **Scalability**: Support 1,000+ concurrent teachers with auto-scaling.
- **Usability**: Intuitive widget configuration; mobile-responsive with touch gestures.
- **Accessibility**: WCAG 2.1 AA compliance with keyboard navigation and screen reader support.
- **Security**: Role-based widget visibility; encrypted data transmission.
- **Reliability**: 99.9% uptime with graceful error handling.

### User Stories
- **As a teacher**, I want to see my class performance at a glance so I can identify areas needing attention.
- **As an educator**, I want quick access to today's lesson plans so I can prepare efficiently.
- **As a teacher**, I want to customize my dashboard layout so I can optimize my workflow.
- **As a substitute teacher**, I want easy access to class information so I can cover effectively.

### Acceptance Criteria
- Dashboard displays 7 core widgets on load.
- Real-time updates occur without page refresh.
- Widgets are fully draggable and resizable.
- Theme toggle works instantly across all components.
- Mobile layout stacks widgets appropriately.
- PD notifications update in real-time.

### Dependencies
- Supabase project with real-time enabled.
- React app with teacher routing.
- Access to teacher-specific data tables.
- Integration with all teacher module components.

### Edge Cases
- Teacher with no assigned classes.
- Network connectivity issues during real-time updates.
- Large number of students per class (>50).
- Multiple concurrent theme/layout changes.

## Technical Specifications

### Technology Stack
- **Frontend**: React 18+ with TypeScript for type-safe component development.
- **Backend**: Node.js 18+ with TypeScript for server-side logic.
- **Database**: Supabase PostgreSQL with real-time capabilities.
- **Authentication**: Supabase Auth with role-based access.
- **Real-time**: Supabase subscriptions for live dashboard updates.
- **UI Library**: Material-UI (MUI) v5 for consistent, accessible components.
- **State Management**: Redux Toolkit for global state (user preferences, notifications).
- **Routing**: React Router v6 for navigation within teacher module.
- **Build Tool**: Vite for fast development and optimized builds.
- **Additional Libraries**: Axios for API calls, React Hook Form for forms, Framer Motion for animations, date-fns for date handling, React DnD for drag-and-drop functionality.

### Architecture
- **Frontend Architecture**: Component-based architecture with custom hooks for data fetching, context providers for theme management, lazy-loaded widgets for performance.
- **Backend Architecture**: Serverless functions via Supabase Edge Functions, RESTful API layer, real-time event broadcasting.
- **Data Flow**: React components → Custom hooks → Supabase client → Database/API → Real-time subscriptions → State updates.
- **Microservices**: Separate services for dashboard data aggregation, notification management, and widget configuration.

### Data Flow
1. Teacher logs in → Supabase Auth verifies role.
2. Dashboard component mounts → Fetches user preferences and layout.
3. Widgets initialize → Query Supabase for relevant data.
4. Real-time subscriptions established → Live updates enabled.
5. User interactions → State updates → Persist to Supabase.

## Frontend Implementation

### Components
- **TeacherDashboard.tsx**: Main container component managing layout and widget rendering.
- **DashboardWidget.tsx**: Reusable wrapper for all dashboard widgets.
- **PersonalOverviewWidget.tsx**: Displays quick stats and KPIs.
- **ClassSummaryWidget.tsx**: Shows class performance data.
- **DailyScheduleWidget.tsx**: Timeline view of today's activities.
- **QuickActionsBar.tsx**: Fixed bar with action buttons.
- **PDNotificationsWidget.tsx**: Professional development alerts.
- **ThemeToggle.tsx**: Dark/light mode switcher.
- **WidgetGrid.tsx**: Drag-and-drop grid layout system.

### UI/UX Designs
- **Layout Structure**:
  - **Header**: User profile, notifications, settings menu, theme toggle.
  - **Main Grid**: 12-column responsive grid with draggable widgets.
  - **Widget Cards**: Consistent card design with headers, content, and action buttons.
  - **Quick Actions Bar**: Fixed bottom bar for instant access.
  - **Mobile Drawer**: Collapsible navigation for smaller screens.
- **Design Principles**: Clean, data-dense interface optimized for productivity; color-coded alerts and status indicators; consistent spacing and typography.

### State Management
- **Redux Slices**: Dashboard slice for widget configurations and layout; User slice for preferences; Notifications slice for PD alerts.
- **Local State**: useState for component-specific interactions (expanded widgets, loading states).
- **Custom Hooks**: useDashboardData for fetching widget data; useRealtimeUpdates for subscription management.

### Routing
- **Routes**: /teacher/dashboard (main), /teacher/{component} for quick actions.
- **Guards**: Teacher role check on mount; redirect for unauthorized access.

### Responsive Design Considerations
- **Breakpoints**: xs (<600px): Single column, stacked widgets; sm (600-900px): 2-column grid; md (900-1200px): 3-column grid; lg (>1200px): 4-column grid.
- **Mobile Optimizations**: Touch-friendly widgets, swipe gestures for navigation, collapsible panels.
- **Tablet/Desktop**: Multi-widget layouts with hover tooltips and keyboard shortcuts.

### Code Example: Personal Overview Widget Component
```tsx
import React, { useEffect, useState } from 'react';
import { Card, CardContent, Typography, Grid, Box } from '@mui/material';
import { supabase } from '../utils/supabaseClient';
import TrendingUpIcon from '@mui/icons-material/TrendingUp';

interface TeacherKPI {
  label: string;
  value: number;
  trend: number;
  unit: string;
  icon: string;
}

const PersonalOverviewWidget: React.FC = () => {
  const [kpis, setKpis] = useState<TeacherKPI[]>([]);

  useEffect(() => {
    const fetchKPIs = async () => {
      const { data: { user } } = await supabase.auth.getUser();
      if (!user) return;

      const { data, error } = await supabase
        .from('teacher_kpis')
        .select('*')
        .eq('teacher_id', user.id);

      if (error) console.error(error);
      else setKpis(data || []);
    };

    fetchKPIs();

    // Real-time subscription
    const subscription = supabase
      .channel('teacher_kpis')
      .on('postgres_changes', { event: '*', schema: 'public', table: 'teacher_kpis' }, fetchKPIs)
      .subscribe();

    return () => subscription.unsubscribe();
  }, []);

  return (
    <Grid container spacing={2}>
      {kpis.map((kpi) => (
        <Grid item xs={12} sm={6} md={3} key={kpi.label}>
          <Card>
            <CardContent>
              <Typography variant="h6">{kpi.label}</Typography>
              <Typography variant="h4" color="primary">
                {kpi.value}{kpi.unit}
              </Typography>
              <Box display="flex" alignItems="center">
                <TrendingUpIcon color={kpi.trend > 0 ? 'success' : 'error'} />
                <Typography variant="body2">
                  {kpi.trend > 0 ? '+' : ''}{kpi.trend}% from last week
                </Typography>
              </Box>
            </CardContent>
          </Card>
        </Grid>
      ))}
    </Grid>
  );
};

export default PersonalOverviewWidget;
```

## Backend Implementation

### Technology Stack
- **Runtime**: Node.js 18+ with TypeScript for server-side logic.
- **Backend Service**: Supabase for database and real-time features.
- **Framework**: Express.js for custom API endpoints; Supabase Edge Functions for serverless logic.
- **Real-time**: Supabase real-time for live dashboard updates.
- **Caching**: Redis (via Supabase) for KPI data caching.
- **Authentication**: Supabase Auth with JWT verification.

### Server-Side Logic
- **KPI Calculation**: Aggregate data from classes, students, and assignments using Supabase queries.
- **Notification Management**: Generate and send PD notifications based on teacher profiles.
- **Data Aggregation**: Scheduled functions to compute dashboard metrics and update real-time.
- **Real-time Broadcasting**: Push updates to connected teacher clients via Supabase channels.

### API Endpoints
- **Supabase Auto-Generated**: RESTful endpoints for teacher data retrieval.
- **Custom Endpoints** (via Edge Functions):
  - GET /functions/v1/teacher/dashboard/kpis: Fetch teacher KPIs.
    - Response: `{ "kpis": [ { "label": "string", "value": number, ... } ] }`
  - POST /functions/v1/teacher/dashboard/layout: Save widget layout.
    - Request: `{ "layout": object }`
    - Response: `{ "success": true }`
  - GET /functions/v1/teacher/dashboard/schedule: Get today's schedule.
    - Response: `{ "lessons": [ { "title": "string", "time": "string", ... } ] }`

### Database Interactions
- **Queries**: Complex aggregations using Supabase's query builder for KPI calculations.
- **Real-time**: Subscriptions for live updates on grades, attendance, and assignments.
- **Caching**: Supabase edge caching for frequently accessed dashboard data.

### Authentication and Authorization
- **Supabase Auth**: JWT-based teacher role verification.
- **RLS Policies**: Restrict dashboard data to assigned teacher and their classes.
- **Role Checks**: Ensure teachers can only access their own data and assigned classes.

### Security Measures
- **Encryption**: Supabase handles data encryption in transit and at rest.
- **Rate Limiting**: Built-in Supabase limits to prevent abuse.
- **Audit Logging**: Track dashboard access and configuration changes.
- **Input Validation**: Sanitize all user inputs to prevent injection attacks.

### Code Example: KPI Calculation Function
```typescript
import { createClient } from '@supabase/supabase-js';

const supabase = createClient(process.env.SUPABASE_URL!, process.env.SUPABASE_SERVICE_ROLE_KEY!);

export const calculateTeacherKPIs = async (teacherId: string) => {
  // Calculate average class attendance
  const { data: classes } = await supabase
    .from('classes')
    .select('id')
    .eq('teacher_id', teacherId);

  if (!classes?.length) return;

  const classIds = classes.map(c => c.id);
  
  const { data: attendance } = await supabase
    .from('attendance')
    .select('present, total_students')
    .in('class_id', classIds)
    .gte('date', new Date(Date.now() - 7 * 24 * 60 * 60 * 1000).toISOString());

  const avgAttendance = attendance?.length 
    ? (attendance.reduce((sum, a) => sum + (a.present / a.total_students), 0) / attendance.length) * 100
    : 0;

  // Calculate assignment completion rate
  const { data: assignments } = await supabase
    .from('assignments')
    .select('id')
    .in('class_id', classIds)
    .gte('due_date', new Date(Date.now() - 7 * 24 * 60 * 60 * 1000).toISOString());

  const assignmentIds = assignments?.map(a => a.id) || [];
  
  const { count: submissions } = await supabase
    .from('assignment_submissions')
    .select('*', { count: 'exact', head: true })
    .in('assignment_id', assignmentIds);

  const totalPossible = assignments?.length * classes.length * 25 || 0; // Assuming 25 students per class
  const completionRate = totalPossible > 0 ? (submissions / totalPossible) * 100 : 0;

  await supabase
    .from('teacher_kpis')
    .upsert({
      teacher_id: teacherId,
      metric: 'avg_attendance',
      label: 'Average Attendance',
      value: Math.round(avgAttendance),
      trend: 0, // Calculate trend separately
      unit: '%'
    });

  await supabase
    .from('teacher_kpis')
    .upsert({
      teacher_id: teacherId,
      metric: 'assignment_completion',
      label: 'Assignment Completion',
      value: Math.round(completionRate),
      trend: 0,
      unit: '%'
    });
};
```

## Database Schema

### Table Structures
- **teacher_kpis**:
  ```sql
  CREATE TABLE teacher_kpis (
    id SERIAL PRIMARY KEY,
    teacher_id UUID REFERENCES users(id) ON DELETE CASCADE,
    metric TEXT NOT NULL,
    label TEXT NOT NULL,
    value NUMERIC NOT NULL,
    trend NUMERIC DEFAULT 0,
    unit TEXT DEFAULT '',
    updated_at TIMESTAMPTZ DEFAULT NOW(),
    UNIQUE(teacher_id, metric)
  );
  ```

- **dashboard_layouts**:
  ```sql
  CREATE TABLE dashboard_layouts (
    id SERIAL PRIMARY KEY,
    teacher_id UUID REFERENCES users(id) ON DELETE CASCADE,
    layout JSONB NOT NULL,
    theme TEXT DEFAULT 'light' CHECK (theme IN ('light', 'dark')),
    updated_at TIMESTAMPTZ DEFAULT NOW()
  );
  ```

- **pd_notifications**:
  ```sql
  CREATE TABLE pd_notifications (
    id SERIAL PRIMARY KEY,
    teacher_id UUID REFERENCES users(id) ON DELETE CASCADE,
    title TEXT NOT NULL,
    message TEXT,
    type TEXT DEFAULT 'info' CHECK (type IN ('info', 'warning', 'success')),
    read BOOLEAN DEFAULT FALSE,
    action_url TEXT,
    created_at TIMESTAMPTZ DEFAULT NOW()
  );
  ```

- **quick_actions**:
  ```sql
  CREATE TABLE quick_actions (
    id SERIAL PRIMARY KEY,
    teacher_id UUID REFERENCES users(id) ON DELETE CASCADE,
    action TEXT NOT NULL,
    label TEXT NOT NULL,
    icon TEXT,
    target_url TEXT,
    order_index INTEGER DEFAULT 0,
    enabled BOOLEAN DEFAULT TRUE
  );
  ```

### Relationships
- teacher_kpis linked to users (teachers).
- dashboard_layouts linked to users.
- pd_notifications linked to users.
- quick_actions linked to users.
- All tables have CASCADE delete for user removal.

### Constraints and Indexes
- Foreign key constraints on teacher_id.
- Unique constraints on teacher_id + metric for KPIs.
- Indexes on teacher_id for all tables.
- Check constraints for theme and notification type.

### Queries
- **Fetch Teacher KPIs**: `SELECT * FROM teacher_kpis WHERE teacher_id = $1 ORDER BY updated_at DESC`.
- **Get Dashboard Layout**: `SELECT layout, theme FROM dashboard_layouts WHERE teacher_id = $1`.
- **Unread PD Notifications**: `SELECT * FROM pd_notifications WHERE teacher_id = $1 AND read = FALSE ORDER BY created_at DESC`.
- **Active Quick Actions**: `SELECT * FROM quick_actions WHERE teacher_id = $1 AND enabled = TRUE ORDER BY order_index`.

### Migrations
- Initial schema creation with all tables.
- Add indexes for performance.
- Add RLS policies for security.
- Future migrations for new KPI types or layout features.

## Data Models

### Teacher KPI Model
```typescript
interface TeacherKPI {
  id: string;
  teacherId: string;
  metric: string;
  label: string;
  value: number;
  trend: number;
  unit: string;
  updatedAt: string;
}

interface DashboardWidget {
  id: string;
  type: 'kpi' | 'summary' | 'schedule' | 'actions' | 'notifications';
  position: { x: number; y: number; width: number; height: number };
  config: Record<string, any>;
  teacherId: string;
}
```

### Class Summary Model
```typescript
interface ClassSummary {
  id: string;
  classId: string;
  className: string;
  studentCount: number;
  avgGrade: number;
  attendanceRate: number;
  assignmentCompletion: number;
  riskStudents: number;
  lastUpdated: string;
}

interface ClassPerformance {
  classId: string;
  subject: string;
  gradeLevel: number;
  period: string;
  metrics: {
    attendance: number;
    participation: number;
    assessment: number;
    homework: number;
  };
  trends: {
    attendance: number;
    grades: number;
  };
}
```

### Daily Schedule Model
```typescript
interface Lesson {
  id: string;
  title: string;
  subject: string;
  classId: string;
  startTime: string;
  endTime: string;
  objectives: string[];
  materials: string[];
  activities: string[];
  notes: string;
}

interface DailySchedule {
  date: string;
  teacherId: string;
  lessons: Lesson[];
  activities: Activity[];
  breaks: Break[];
}

interface Activity {
  id: string;
  title: string;
  type: 'assessment' | 'project' | 'discussion' | 'lab';
  duration: number;
  classId: string;
  completed: boolean;
}
```

### Professional Development Model
```typescript
interface PDNotification {
  id: string;
  teacherId: string;
  title: string;
  message: string;
  type: 'info' | 'warning' | 'success';
  read: boolean;
  actionUrl?: string;
  createdAt: string;
  expiresAt?: string;
}

interface PDOpportunity {
  id: string;
  title: string;
  description: string;
  provider: string;
  startDate: string;
  endDate: string;
  credits: number;
  cost: number;
  format: 'online' | 'in-person' | 'hybrid';
  recommendedFor: string[];
}

interface TeacherPDProfile {
  teacherId: string;
  completedCourses: string[];
  currentEnrollments: string[];
  certifications: Certification[];
  interests: string[];
  goals: string[];
}

interface Certification {
  id: string;
  name: string;
  issuer: string;
  issueDate: string;
  expiryDate: string;
  renewalRequired: boolean;
}
```

### Dashboard Layout Model
```typescript
interface DashboardLayout {
  id: string;
  teacherId: string;
  layout: WidgetLayout[];
  theme: 'light' | 'dark';
  updatedAt: string;
}

interface WidgetLayout {
  id: string;
  type: string;
  position: { x: number; y: number };
  size: { width: number; height: number };
  config: Record<string, any>;
  visible: boolean;
}

interface UserPreferences {
  teacherId: string;
  theme: 'light' | 'dark' | 'auto';
  language: string;
  timezone: string;
  notifications: NotificationSettings;
  accessibility: AccessibilitySettings;
}

interface NotificationSettings {
  email: boolean;
  push: boolean;
  pdAlerts: boolean;
  classAlerts: boolean;
  systemAlerts: boolean;
}

interface AccessibilitySettings {
  highContrast: boolean;
  largeText: boolean;
  reduceMotion: boolean;
  screenReader: boolean;
}
```

### Quick Actions Model
```typescript
interface QuickAction {
  id: string;
  teacherId: string;
  action: string;
  label: string;
  icon: string;
  targetUrl: string;
  orderIndex: number;
  enabled: boolean;
  shortcut?: string;
}

interface ActionConfig {
  action: string;
  requiresConfirmation: boolean;
  parameters: Record<string, any>;
  permissions: string[];
}
```

## API Design

### Endpoints
- **Supabase REST**: /rest/v1/teacher_kpis, /rest/v1/dashboard_layouts, /rest/v1/pd_notifications, /rest/v1/quick_actions.
- **Real-time Channels**: teacher_dashboard_{teacherId}, pd_notifications_{teacherId}.

### Request/Response Formats
- **JSON Standard**: Consistent structure for all responses with metadata.
- **Pagination**: For large datasets like notifications or schedule items.
- **Filtering**: Query parameters for date ranges, class filters, etc.

### Error Handling
- **Status Codes**: 200 (success), 400 (bad request), 401 (unauthorized), 403 (forbidden), 404 (not found), 500 (server error).
- **Error Format**: `{ "error": { "code": "string", "message": "string", "details": "object" } }`
- **Validation Errors**: Field-specific error messages for form submissions.

### Integration with Supabase
- **Real-time**: Automatic updates via subscriptions for live dashboard data.
- **Caching**: Supabase edge caching for improved performance.
- **Auth**: JWT tokens for secure API access.
- **RLS**: Row-level security policies for data access control.

## Testing Strategy

### Unit Tests
- **Tools**: Jest with React Testing Library for component testing.
- **Coverage**: Test KPI calculations, widget rendering, theme switching, drag-and-drop functionality.
- **Mocking**: Mock Supabase client for isolated testing.

### Integration Tests
- **Tools**: Jest with Supertest for API testing.
- **Scenarios**: Test Supabase queries, real-time subscriptions, data aggregation functions.
- **Database**: Use test database with seeded data.

### End-to-End Tests
- **Tools**: Cypress for browser automation.
- **Flows**: Load dashboard, interact with widgets, test real-time updates, verify responsive design.
- **Coverage**: Critical user journeys like customizing layout, accessing quick actions, viewing notifications.

### Tools/Frameworks
- Jest for unit/integration testing.
- React Testing Library for component testing.
- Cypress for E2E testing.
- Supertest for API testing.

### Test Data Management
- **Fixtures**: Pre-defined test data for teachers, classes, students.
- **Factories**: Dynamic test data generation for various scenarios.
- **Cleanup**: Automatic test data cleanup after test execution.

## Deployment and DevOps

### CI/CD Pipelines
- **GitHub Actions**: Automated testing, building, and deployment to Vercel/Netlify.
- **Steps**: 
  1. Lint and type-check code.
  2. Run unit and integration tests.
  3. Build optimized production bundle.
  4. Deploy to staging environment.
  5. Run E2E tests on staging.
  6. Deploy to production.
- **Triggers**: Push to main branch, pull request creation.

### Environment Configurations
- **Development**: Local Supabase instance with mock data, hot reloading enabled.
- **Staging**: Full Supabase deployment with production-like data, automated testing.
- **Production**: Optimized Supabase deployment with real-time data, monitoring, and auto-scaling.
- **Secrets Management**: Secure handling of API keys, database URLs, and sensitive configuration.

### Scalability Considerations
- **Supabase Scaling**: Automatic database scaling based on load.
- **CDN**: Vercel/Netlify global CDN for fast content delivery.
- **Caching**: Supabase edge functions for API response caching.
- **Load Balancing**: Built-in load balancing for high-traffic periods.

### Monitoring
- **Application Monitoring**: Vercel Analytics for performance metrics, error tracking.
- **Database Monitoring**: Supabase dashboard for query performance, connection counts.
- **Real-time Monitoring**: Track subscription connections, update frequencies.
- **User Monitoring**: Track feature usage, error rates, user satisfaction.

### Rollback Procedures
- **Versioned Deployments**: Git tags for each release.
- **Quick Rollback**: One-click rollback to previous version in Vercel/Netlify.
- **Database Rollback**: Supabase point-in-time recovery for data issues.
- **Monitoring During Rollback**: Ensure system stability post-rollback.

## Security Considerations

### Authentication Mechanisms
- **Supabase Auth**: Secure JWT-based authentication with refresh tokens.
- **Multi-Factor Authentication**: Optional 2FA for enhanced security.
- **Session Management**: Automatic session timeout, secure logout.

### Data Encryption
- **In Transit**: TLS 1.3 encryption for all data transmission.
- **At Rest**: Supabase automatic encryption of sensitive data.
- **Client-Side**: Encrypt sensitive user preferences before storage.

### GDPR/FERPA Compliance
- **Data Minimization**: Only collect necessary teacher and student data.
- **Consent Management**: Clear consent for data processing.
- **Right to Access**: Teachers can access their own data and request student data deletion.
- **Data Retention**: Automatic deletion of old logs and temporary data.
- **FERPA Compliance**: Strict access controls for student data, audit logging of access.

### Access Control
- **Role-Based Access**: Teacher role required for dashboard access.
- **Row-Level Security**: RLS policies restrict data access to assigned classes.
- **Permission Checks**: Validate permissions for each action (view grades, send messages).

### Vulnerability Mitigations
- **Input Validation**: Sanitize all user inputs to prevent XSS, SQL injection.
- **Rate Limiting**: Prevent abuse with request throttling.
- **Security Headers**: Implement CSP, HSTS, X-Frame-Options.
- **Dependency Scanning**: Regular security audits of npm packages.
- **Regular Updates**: Keep all dependencies and Supabase updated.

### Audit Logging
- **Access Logs**: Track dashboard access, widget interactions.
- **Data Changes**: Log modifications to layouts, preferences.
- **Security Events**: Monitor failed login attempts, suspicious activities.

## Performance Optimization

### Frontend Optimizations
- **Code Splitting**: Lazy load dashboard widgets using React.lazy().
- **Bundle Optimization**: Use Vite for efficient bundling and tree shaking.
- **Image Optimization**: Compress and serve images via CDN.
- **Caching**: Browser caching for static assets, Redux for state caching.

### Backend Optimizations
- **Query Optimization**: Use database indexes, optimize complex queries.
- **Caching**: Supabase edge caching for frequent API calls.
- **Connection Pooling**: Efficient database connection management.
- **Async Processing**: Background jobs for heavy computations.

### Real-time Optimizations
- **Subscription Management**: Efficient channel management to reduce server load.
- **Debounced Updates**: Batch rapid updates to reduce network traffic.
- **Selective Updates**: Only send relevant updates to connected clients.

### Monitoring and Metrics
- **Core Web Vitals**: Monitor LCP, FID, CLS for optimal user experience.
- **API Performance**: Track response times, error rates.
- **Database Performance**: Monitor query execution times, connection counts.
- **Real-time Metrics**: Track subscription latency, update frequencies.

## Edge Cases and Error Handling

### Common Issues
- **Network Connectivity**: Offline mode with cached data display.
- **Real-time Disconnection**: Auto-reconnect with exponential backoff.
- **Large Datasets**: Pagination and virtualization for performance.
- **Browser Compatibility**: Fallbacks for older browsers.

### Fallback Mechanisms
- **Widget Failures**: Show error state with retry button.
- **API Failures**: Display cached data with offline indicator.
- **Theme Failures**: Default to light mode if custom theme fails.
- **Layout Corruption**: Reset to default layout if configuration is invalid.

### User Feedback
- **Loading States**: Skeleton screens for widgets during data fetch.
- **Error Messages**: Clear, actionable error messages with support contact.
- **Toast Notifications**: Non-intrusive feedback for actions and errors.
- **Progress Indicators**: Show progress for long-running operations.

### Graceful Degradation
- **Feature Flags**: Disable advanced features if dependencies fail.
- **Progressive Enhancement**: Core functionality works without JavaScript.
- **Responsive Fallbacks**: Ensure usability on all screen sizes.

## Integration Points

### Cross-Module Integrations
- **Academic Management**: Pull grades, attendance, class schedules.
- **User Management**: Access teacher profiles, student information.
- **Communication Hub**: Send/receive messages, notifications.
- **Student Progress Tracking**: Detailed analytics and insights.
- **Lesson Planning**: Access and display lesson plans.
- **Assignments & Assessments**: Quick access to create/manage assignments.
- **Resources & Materials**: Link to teaching materials.
- **Reports & Analytics**: Export dashboard data for reports.
- **Professional Development**: PD opportunities and tracking.
- **Profile & Settings**: User preferences and configurations.

### Dependencies
- **Internal**: All teacher module components for data and navigation.
- **External**: Supabase ecosystem for database, auth, real-time features.

### Data Synchronization
- **Real-time Sync**: Live updates across all integrated modules.
- **Batch Updates**: Scheduled synchronization for non-critical data.
- **Conflict Resolution**: Handle concurrent edits gracefully.

## Code Examples

### Dashboard Layout Component with Drag-and-Drop
```tsx
import React, { useState, useEffect } from 'react';
import { DndProvider } from 'react-dnd';
import { HTML5Backend } from 'react-dnd-html5-backend';
import { Grid, Paper } from '@mui/material';
import { supabase } from '../utils/supabaseClient';

interface Widget {
  id: string;
  type: string;
  x: number;
  y: number;
  width: number;
  height: number;
}

const DashboardGrid: React.FC = () => {
  const [widgets, setWidgets] = useState<Widget[]>([]);
  const [layout, setLayout] = useState<any>(null);

  useEffect(() => {
    const loadLayout = async () => {
      const { data: { user } } = await supabase.auth.getUser();
      if (!user) return;

      const { data } = await supabase
        .from('dashboard_layouts')
        .select('layout')
        .eq('teacher_id', user.id)
        .single();

      if (data?.layout) {
        setLayout(data.layout);
        setWidgets(data.layout.widgets || []);
      }
    };

    loadLayout();
  }, []);

  const saveLayout = async (newWidgets: Widget[]) => {
    const { data: { user } } = await supabase.auth.getUser();
    if (!user) return;

    await supabase
      .from('dashboard_layouts')
      .upsert({
        teacher_id: user.id,
        layout: { widgets: newWidgets }
      });
  };

  const moveWidget = (id: string, x: number, y: number) => {
    const newWidgets = widgets.map(widget =>
      widget.id === id ? { ...widget, x, y } : widget
    );
    setWidgets(newWidgets);
    saveLayout(newWidgets);
  };

  return (
    <DndProvider backend={HTML5Backend}>
      <Grid container spacing={2}>
        {widgets.map(widget => (
          <Grid item xs={widget.width} key={widget.id}>
            <Paper 
              sx={{ 
                height: widget.height * 100,
                p: 2,
                cursor: 'move'
              }}
              draggable
              onDragEnd={(e) => {
                const rect = e.currentTarget.getBoundingClientRect();
                moveWidget(widget.id, rect.left, rect.top);
              }}
            >
              {/* Widget content based on type */}
              <div>Widget {widget.type}</div>
            </Paper>
          </Grid>
        ))}
      </Grid>
    </DndProvider>
  );
};

export default DashboardGrid;
```

### Real-time PD Notifications Hook
```tsx
import { useEffect, useState } from 'react';
import { supabase } from '../utils/supabaseClient';

interface PDNotification {
  id: string;
  title: string;
  message: string;
  type: 'info' | 'warning' | 'success';
  read: boolean;
}

export const usePDNotifications = () => {
  const [notifications, setNotifications] = useState<PDNotification[]>([]);

  useEffect(() => {
    const fetchNotifications = async () => {
      const { data: { user } } = await supabase.auth.getUser();
      if (!user) return;

      const { data } = await supabase
        .from('pd_notifications')
        .select('*')
        .eq('teacher_id', user.id)
        .order('created_at', { ascending: false });

      setNotifications(data || []);
    };

    fetchNotifications();

    const subscription = supabase
      .channel('pd_notifications')
      .on('postgres_changes', { 
        event: '*', 
        schema: 'public', 
        table: 'pd_notifications' 
      }, (payload) => {
        if (payload.eventType === 'INSERT') {
          setNotifications(prev => [payload.new as PDNotification, ...prev]);
        } else if (payload.eventType === 'UPDATE') {
          setNotifications(prev => 
            prev.map(n => n.id === payload.new.id ? payload.new as PDNotification : n)
          );
        }
      })
      .subscribe();

    return () => subscription.unsubscribe();
  }, []);

  const markAsRead = async (id: string) => {
    await supabase
      .from('pd_notifications')
      .update({ read: true })
      .eq('id', id);

    setNotifications(prev => 
      prev.map(n => n.id === id ? { ...n, read: true } : n)
    );
  };

  return { notifications, markAsRead };
};
```

### Theme Toggle with Persistence
```tsx
import React, { createContext, useContext, useEffect, useState } from 'react';
import { ThemeProvider, createTheme } from '@mui/material/styles';
import { supabase } from '../utils/supabaseClient';

type ThemeMode = 'light' | 'dark';

interface ThemeContextType {
  mode: ThemeMode;
  toggleTheme: () => void;
}

const ThemeContext = createContext<ThemeContextType | undefined>(undefined);

export const useTheme = () => {
  const context = useContext(ThemeContext);
  if (!context) throw new Error('useTheme must be used within ThemeProvider');
  return context;
};

interface ThemeProviderProps {
  children: React.ReactNode;
}

export const AppThemeProvider: React.FC<ThemeProviderProps> = ({ children }) => {
  const [mode, setMode] = useState<ThemeMode>('light');

  useEffect(() => {
    const loadTheme = async () => {
      const { data: { user } } = await supabase.auth.getUser();
      if (!user) return;

      const { data } = await supabase
        .from('dashboard_layouts')
        .select('theme')
        .eq('teacher_id', user.id)
        .single();

      if (data?.theme) {
        setMode(data.theme);
      } else {
        // Check system preference
        const systemPrefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
        setMode(systemPrefersDark ? 'dark' : 'light');
      }
    };

    loadTheme();
  }, []);

  const toggleTheme = async () => {
    const newMode = mode === 'light' ? 'dark' : 'light';
    setMode(newMode);

    const { data: { user } } = await supabase.auth.getUser();
    if (user) {
      await supabase
        .from('dashboard_layouts')
        .upsert({
          teacher_id: user.id,
          theme: newMode
        }, { onConflict: 'teacher_id' });
    }
  };

  const theme = createTheme({
    palette: {
      mode,
      primary: { main: mode === 'dark' ? '#90caf9' : '#1976d2' },
      secondary: { main: mode === 'dark' ? '#f48fb1' : '#dc004e' },
    },
  });

  return (
    <ThemeContext.Provider value={{ mode, toggleTheme }}>
      <ThemeProvider theme={theme}>
        {children}
      </ThemeProvider>
    </ThemeContext.Provider>
  );
};
```

## Dependencies and Libraries

### Frontend Dependencies
- **React**: ^18.2.0 - Core UI library
- **TypeScript**: ^4.9.0 - Type safety
- **@mui/material**: ^5.11.0 - UI component library
- **@emotion/react**: ^11.10.0 - CSS-in-JS
- **@emotion/styled**: ^11.10.0 - Styled components
- **@supabase/supabase-js**: ^2.7.0 - Supabase client
- **react-redux**: ^8.0.5 - State management
- **@reduxjs/toolkit**: ^1.9.0 - Redux utilities
- **react-router-dom**: ^6.8.0 - Routing
- **axios**: ^1.3.0 - HTTP client
- **react-hook-form**: ^7.43.0 - Form handling
- **framer-motion**: ^10.0.0 - Animations
- **date-fns**: ^2.29.0 - Date utilities
- **react-dnd**: ^16.0.0 - Drag and drop
- **react-dnd-html5-backend**: ^16.0.0 - DnD backend

### Backend Dependencies
- **@supabase/supabase-js**: ^2.7.0 - Supabase client
- **@supabase/functions-js**: ^2.1.0 - Edge functions

### Development Dependencies
- **@types/react**: ^18.0.0 - React types
- **@types/react-dom**: ^18.0.0 - React DOM types
- **@typescript-eslint/eslint-plugin**: ^5.50.0 - TypeScript ESLint
- **@typescript-eslint/parser**: ^5.50.0 - TypeScript parser
- **eslint**: ^8.33.0 - Linting
- **prettier**: ^2.8.0 - Code formatting
- **jest**: ^29.4.0 - Testing framework
- **@testing-library/react**: ^13.4.0 - React testing utilities
- **@testing-library/jest-dom**: ^5.16.0 - Jest DOM matchers
- **cypress**: ^12.5.0 - E2E testing
- **vite**: ^4.1.0 - Build tool
- **@vitejs/plugin-react**: ^3.1.0 - Vite React plugin

### DevOps Dependencies
- **vercel**: ^28.0.0 - Deployment platform
- **supabase**: ^1.25.0 - Supabase CLI

## Future Enhancements

### AI-Powered Features
- **Smart Scheduling**: AI recommendations for optimal lesson timing based on student performance data.
- **Personalized PD**: AI-curated professional development opportunities based on teaching style and student needs.
- **Predictive Analytics**: Machine learning models to predict student performance issues before they occur.

### Advanced Customizations
- **Widget Marketplace**: Community-contributed dashboard widgets with teacher ratings and reviews.
- **Advanced Layouts**: Multi-page dashboards with conditional widget visibility based on time or context.
- **Custom Widget Builder**: No-code widget creation tool for teachers to build personalized data views.

### Mobile and Cross-Platform Features
- **Progressive Web App**: Installable dashboard for offline access and native-like experience.
- **Mobile-Specific Widgets**: Touch-optimized widgets for tablets and phones.
- **Cross-Device Sync**: Seamless synchronization of layouts and preferences across devices.

### Enhanced Real-time Features
- **Live Collaboration**: Real-time co-editing of lesson plans and assignments.
- **Instant Messaging**: Integrated chat within dashboard for quick teacher communication.
- **Live Polling**: Real-time student response collection during lessons.

### Analytics and Insights
- **Advanced Reporting**: Custom report generation with AI-powered insights.
- **Trend Analysis**: Long-term performance trends with predictive modeling.
- **Peer Comparisons**: Anonymous comparison with similar teachers for benchmarking.

### Integration Expansions
- **Third-Party Tools**: Integration with popular educational platforms (Google Classroom, Canvas).
- **IoT Integration**: Smart classroom device monitoring and control.
- **API Ecosystem**: Public APIs for third-party dashboard extensions.