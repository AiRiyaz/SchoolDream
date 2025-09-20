# SchoolDream Admin Dashboard Feature Documentation

## Overview

The Admin Dashboard serves as the central command center for school administrators in the SchoolDream platform, providing a comprehensive overview of institutional performance, real-time insights, and quick access to critical management functions. It aggregates data from across the platform to enable data-driven decision-making, proactive issue resolution, and efficient resource management.

### Purpose
- **Primary Goal**: Deliver actionable insights through visual KPIs, enable rapid response to alerts, and provide streamlined access to administrative functions.
- **Key Objectives**: Monitor system health, track key performance indicators, manage resources efficiently, and facilitate quick navigation to detailed management areas.
- **Scope**: Real-time data visualization, interactive widgets, customizable layouts, and integration with all admin module components.

### Target Users
- **School Administrators**: Principals, vice-principals, and administrative staff responsible for institutional oversight.
- **IT Administrators**: Technical staff managing system performance and infrastructure.
- **Department Heads**: Academic leaders monitoring departmental performance.

### Integration with SchoolDream Platform
- **Data Sources**: Pulls from all modules (User Management, Academic Management, Financial Management, etc.) via Supabase real-time subscriptions.
- **Navigation Hub**: Provides shortcuts to all 11 core admin components.
- **Alert System**: Integrates with Communication Hub for broadcasting alerts.
- **Analytics Engine**: Feeds into Reports & Analytics module for deeper insights.

## Requirements

### Functional Requirements
- **KPI Display**: Show key metrics with visual indicators (charts, graphs, gauges).
- **Real-time Alerts**: Display system-wide notifications with priority levels.
- **Quick Access Shortcuts**: Provide one-click navigation to frequently used functions.
- **System-wide Metrics**: Aggregate and display institutional performance data.
- **Upcoming Events Calendar**: Show scheduled events with interactive calendar view.
- **Resource Utilization Statistics**: Display usage metrics for facilities, staff, and systems.
- **Customizable Widgets**: Allow admins to rearrange and configure dashboard elements.
- **Data Export**: Enable downloading of dashboard data in various formats.

### Non-Functional Requirements
- **Performance**: Dashboard loads in < 2 seconds; real-time updates with < 1 second latency.
- **Scalability**: Support 100+ concurrent admin users with auto-scaling.
- **Usability**: Intuitive drag-and-drop widget configuration; mobile-responsive design.
- **Accessibility**: WCAG 2.1 AA compliance with keyboard navigation and screen reader support.
- **Security**: Role-based widget visibility; encrypted data transmission.

### User Stories
- **As an administrator**, I want to see KPIs at a glance so I can quickly assess institutional health.
- **As an admin**, I want real-time alerts for critical issues so I can respond immediately.
- **As a principal**, I want quick shortcuts to user management so I can handle urgent tasks.
- **As an IT admin**, I want resource utilization stats so I can optimize infrastructure.

### Acceptance Criteria
- Dashboard displays 6 core KPI widgets on load.
- Alerts update in real-time without page refresh.
- Shortcuts reduce navigation clicks by 50%.
- Calendar shows events with color-coded categories.
- Utilization charts update every 5 minutes.
- Widgets are draggable and resizable.

### Dependencies
- Supabase project with real-time enabled.
- React app with dashboard routing.
- Access to all admin module data tables.

## Frontend Implementation

### Technology Stack
- **Framework**: React 18+ with TypeScript for type-safe component development.
- **UI Library**: Material-UI (MUI) v5 for consistent, accessible components; Chart.js or Recharts for data visualization.
- **State Management**: Redux Toolkit for global state (alerts, user preferences).
- **Routing**: React Router v6 for navigation to admin components.
- **Real-time**: Supabase real-time subscriptions for live updates.
- **Additional Libraries**: React DnD for drag-and-drop widgets; date-fns for calendar handling.

### UI/UX Designs
- **Layout Structure**:
  - **Header**: User profile, notification bell, settings menu.
  - **Main Grid**: 12-column responsive grid with draggable widgets.
  - **KPI Widgets**: Cards with icons, values, and trend indicators.
  - **Alert Panel**: Collapsible sidebar with prioritized notifications.
  - **Shortcut Bar**: Fixed bottom bar with quick action buttons.
  - **Calendar Widget**: Mini-calendar with event popovers.
  - **Footer**: System status and last updated timestamp.
- **Design Principles**: Clean, data-dense interface with color-coded alerts; dark/light mode support.

### Components
- **DashboardGrid.tsx**: Main container with drag-and-drop functionality.
- **KPIWidget.tsx**: Reusable widget for metrics display.
- **AlertPanel.tsx**: Notification list with filtering.
- **ShortcutBar.tsx**: Quick access buttons.
- **CalendarWidget.tsx**: Interactive calendar component.
- **UtilizationChart.tsx**: Charts for resource statistics.

### State Management
- **Redux Slices**: Dashboard slice for widget configuration; Alerts slice for notifications.
- **Local State**: useState for component-specific data (e.g., expanded widgets).

### Routing
- **Routes**: /admin/dashboard (main), /admin/{component} for shortcuts.
- **Guards**: Admin role check on mount.

### Responsive Design Considerations
- **Breakpoints**: xs (widgets stack), sm (2-column), md (3-column), lg (4-column).
- **Mobile Optimizations**: Swipe gestures for widgets; collapsible panels.
- **Tablet/Desktop**: Multi-widget layouts with hover tooltips.

### Code Example: KPI Widget Component
```tsx
import React, { useEffect, useState } from 'react';
import { Card, CardContent, Typography, Box } from '@mui/material';
import { supabase } from '../utils/supabaseClient';
import TrendingUpIcon from '@mui/icons-material/TrendingUp';

interface KPIMetric {
  label: string;
  value: number;
  trend: number;
  unit: string;
}

const KPIWidget: React.FC<{ metric: string }> = ({ metric }) => {
  const [data, setData] = useState<KPIMetric | null>(null);

  useEffect(() => {
    const fetchKPI = async () => {
      const { data, error } = await supabase
        .from('kpi_metrics')
        .select('*')
        .eq('metric', metric)
        .single();
      if (error) console.error(error);
      else setData(data);
    };

    fetchKPI();

    // Real-time subscription
    const subscription = supabase
      .channel('kpi_updates')
      .on('postgres_changes', { event: 'UPDATE', schema: 'public', table: 'kpi_metrics' }, fetchKPI)
      .subscribe();

    return () => subscription.unsubscribe();
  }, [metric]);

  if (!data) return <div>Loading...</div>;

  return (
    <Card sx={{ minWidth: 275 }}>
      <CardContent>
        <Typography variant="h5" component="div">
          {data.label}
        </Typography>
        <Typography variant="h4" color="primary">
          {data.value} {data.unit}
        </Typography>
        <Box display="flex" alignItems="center">
          <TrendingUpIcon color={data.trend > 0 ? 'success' : 'error'} />
          <Typography variant="body2">
            {data.trend > 0 ? '+' : ''}{data.trend}% from last period
          </Typography>
        </Box>
      </CardContent>
    </Card>
  );
};

export default KPIWidget;
```

## Backend Implementation

### Technology Stack
- **Runtime**: Node.js 18+ with TypeScript for server-side logic.
- **Backend Service**: Supabase for database and real-time features.
- **Framework**: Express.js for custom API endpoints; Supabase Edge Functions for serverless logic.
- **Real-time**: Supabase real-time for live dashboard updates.
- **Caching**: Redis (via Supabase) for KPI data caching.

### Server-Side Logic
- **KPI Calculation**: Aggregate data from multiple tables (users, classes, payments) using Supabase queries.
- **Alert Generation**: Monitor thresholds and trigger notifications via Supabase functions.
- **Data Aggregation**: Scheduled functions to compute metrics and update dashboard data.
- **Real-time Broadcasting**: Push updates to connected clients via Supabase channels.

### API Endpoints
- **Supabase Auto-Generated**: RESTful endpoints for KPI data retrieval.
- **Custom Endpoints** (via Edge Functions):
  - GET /functions/v1/dashboard/kpis: Fetch all KPI metrics.
    - Response: `{ "metrics": [ { "label": "string", "value": number, ... } ] }`
  - POST /functions/v1/dashboard/alerts: Create new alert.
    - Request: `{ "message": "string", "priority": "high|medium|low" }`
    - Response: `{ "success": true }`

### Database Interactions
- **Queries**: Complex aggregations using Supabase's query builder.
- **Real-time**: Subscriptions for live KPI updates.

### Authentication and Authorization
- **Supabase Auth**: JWT-based admin role verification.
- **RLS Policies**: Restrict dashboard data to admin users.

### Security Measures
- **Encryption**: Supabase handles data encryption.
- **Rate Limiting**: Built-in Supabase limits.
- **Audit Logging**: Track dashboard access and changes.

### Code Example: KPI Calculation Function
```typescript
import { createClient } from '@supabase/supabase-js';

const supabase = createClient(process.env.SUPABASE_URL!, process.env.SUPABASE_SERVICE_ROLE_KEY!);

export const calculateKPIs = async () => {
  // Example: Calculate total students
  const { count: totalStudents } = await supabase
    .from('students')
    .select('*', { count: 'exact', head: true });

  // Calculate trend (simplified)
  const lastMonth = new Date();
  lastMonth.setMonth(lastMonth.getMonth() - 1);
  const { count: lastMonthStudents } = await supabase
    .from('students')
    .select('*', { count: 'exact', head: true })
    .lt('created_at', lastMonth);

  const trend = totalStudents && lastMonthStudents
    ? ((totalStudents - lastMonthStudents) / lastMonthStudents) * 100
    : 0;

  await supabase
    .from('kpi_metrics')
    .upsert({
      metric: 'total_students',
      label: 'Total Students',
      value: totalStudents || 0,
      trend,
      unit: ''
    });
};
```

## Database Schema

### Table Structures
- **kpi_metrics**:
  ```sql
  CREATE TABLE kpi_metrics (
    id SERIAL PRIMARY KEY,
    metric TEXT UNIQUE NOT NULL,
    label TEXT NOT NULL,
    value NUMERIC NOT NULL,
    trend NUMERIC DEFAULT 0,
    unit TEXT DEFAULT '',
    updated_at TIMESTAMPTZ DEFAULT NOW()
  );
  ```
- **alerts**:
  ```sql
  CREATE TABLE alerts (
    id SERIAL PRIMARY KEY,
    message TEXT NOT NULL,
    priority TEXT CHECK (priority IN ('high', 'medium', 'low')) DEFAULT 'medium',
    created_at TIMESTAMPTZ DEFAULT NOW(),
    resolved BOOLEAN DEFAULT FALSE
  );
  ```
- **events** (for calendar):
  ```sql
  CREATE TABLE events (
    id SERIAL PRIMARY KEY,
    title TEXT NOT NULL,
    description TEXT,
    start_date TIMESTAMPTZ NOT NULL,
    end_date TIMESTAMPTZ,
    category TEXT DEFAULT 'general'
  );
  ```

### Relationships
- Alerts linked to users via separate table if needed.
- Events can reference classes or users.

### Queries
- **Fetch KPIs**: `SELECT * FROM kpi_metrics ORDER BY updated_at DESC`.
- **Active Alerts**: `SELECT * FROM alerts WHERE resolved = FALSE ORDER BY priority DESC, created_at DESC`.

## API Design

### Endpoints
- **Supabase REST**: /rest/v1/kpi_metrics, /rest/v1/alerts, /rest/v1/events.
- **Real-time Channels**: dashboard_kpis, dashboard_alerts.

### Request/Response Formats
- **JSON Standard**: Consistent structure for all responses.
- **Pagination**: For large datasets (e.g., events).

### Error Handling
- **Status Codes**: 200 (success), 401 (unauthorized), 500 (error).
- **Error Format**: `{ "error": { "message": "string", "details": "object" } }`

### Integration with Supabase
- **Real-time**: Automatic updates via subscriptions.
- **Caching**: Supabase edge caching for performance.

## Testing Strategy

### Unit Tests
- **Tools**: Jest with React Testing Library.
- **Coverage**: Test KPI calculations, widget rendering.

### Integration Tests
- **Tools**: Jest with Supertest.
- **Scenarios**: Test Supabase queries and real-time updates.

### End-to-End Tests
- **Tools**: Cypress.
- **Flows**: Load dashboard, interact with widgets, verify updates.

### Tools/Frameworks
- Jest for unit/integration; Cypress for E2E.

## Deployment and DevOps

### CI/CD Pipelines
- **GitHub Actions**: Automate tests and deployment to Vercel.
- **Steps**: Lint, test, build, deploy.

### Environment Configurations
- **Production**: Full Supabase deployment with real-time data, monitoring, and auto-scaling.
- **Pre-Production**: Environment for final validation with production-like data.
- **Secrets**: Secure handling of API keys and sensitive data.

### Scalability Considerations
- **Supabase Scaling**: Automatic for database and functions.
- **CDN**: Vercel for global distribution.

### Monitoring
- **Tools**: Vercel Analytics; Supabase Dashboard.
- **Metrics**: Dashboard load times, error rates.

## Security Considerations

### Data Protection
- **Encryption**: Supabase TLS 1.3.
- **Compliance**: FERPA/GDPR for educational data.

### Access Control
- **RBAC**: Admin-only access.
- **RLS**: Policies on tables.

### Vulnerabilities
- **Mitigation**: Input validation; regular updates.

## Performance Optimization

### Frontend
- **Lazy Loading**: React.lazy for widgets.
- **Caching**: Redux for state; browser caching.

### Backend
- **Query Optimization**: Indexed tables.
- **Caching**: Supabase for frequent queries.

### General
- **Compression**: Gzip on responses.
- **Monitoring**: Track performance metrics.

## Edge Cases and Error Handling

### Common Issues
- **Network Failures**: Offline mode with cached data.
- **Data Errors**: Fallback to default values.
- **Real-time Disconnects**: Auto-reconnect with Supabase.

### Fallback Mechanisms
- **Widget Failures**: Show error message; retry fetch.
- **Alert Overload**: Paginate or summarize.

### User Feedback
- **Loading States**: Skeletons for widgets.
- **Notifications**: Toast for errors.

## Integration Points

### With Other Modules
- **User Management**: Fetch user counts for KPIs.
- **Financial Management**: Payment metrics.
- **Reports & Analytics**: Export dashboard data.

### Dependencies
- **Internal**: All admin components.
- **External**: Supabase ecosystem.

## Code Examples

See examples in Frontend and Backend sections.

## Dependencies and Libraries

- **Frontend**: react, typescript, @mui/material, reduxjs/toolkit, recharts, react-dnd, @supabase/supabase-js.
- **Backend**: @supabase/supabase-js, typescript.
- **Dev Tools**: jest, @testing-library/react, cypress.

## Future Enhancements

- **AI Insights**: Predictive analytics in widgets.
- **Custom Dashboards**: Per-admin configurations.
- **Mobile App**: Native dashboard for admins.
- **Advanced Visualizations**: 3D charts, AR overlays.
- **Integration APIs**: Third-party dashboard tools.

This documentation enables independent development of the Admin Dashboard feature.