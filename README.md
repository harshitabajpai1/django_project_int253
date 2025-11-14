# EcoDriving Tracker

A comprehensive web application built with Django and Supabase to help users track and improve their driving habits, promoting fuel efficiency and eco-friendly behavior.

## Features

### Core Functionality
- **User Authentication**: Secure signup/login system using Django authentication
- **Trip Tracking**: Record detailed driving data including:
  - Distance traveled
  - Trip duration
  - Average and maximum speed
  - Hard braking events
  - Hard acceleration events
  - Idling time

### Eco Score System
- **Automatic Calculation**: Each trip receives an Eco Score (0-100) based on:
  - Speed management
  - Braking patterns
  - Acceleration behavior
  - Idling time
  - Overall driving efficiency
- **Fuel Efficiency Estimation**: Estimated fuel consumption (L/100km) based on driving behavior

### Dashboard & Analytics
- **Performance Overview**: View total trips, average eco score, and total distance
- **Interactive Charts**: Visualize performance trends with Chart.js
- **Recent Trips**: Quick access to your latest driving records
- **Statistics**: Comprehensive driving metrics and insights

### Personalized Recommendations
- **Smart Tips**: Receive customized eco-driving tips based on your specific driving patterns
- **Category-Based Advice**: Tips covering:
  - Braking techniques
  - Acceleration optimization
  - Speed management
  - Idling reduction
  - General best practices

### Leaderboard
- **Global Rankings**: See how you rank against other eco-conscious drivers
- **Top 20 Display**: View the best performers with medal indicators
- **Personal Ranking**: Track your position and progress

### Reporting
- **PDF Export**: Download professionally formatted PDF reports with:
  - Summary statistics
  - Recent trip history
  - Performance metrics
  - Custom branding

## Technology Stack

- **Backend**: Django 5.0
- **Database**: Supabase (PostgreSQL)
- **Frontend**: Bootstrap 5, Chart.js
- **PDF Generation**: ReportLab
- **Authentication**: Django Auth System

## Installation

### Prerequisites
- Python 3.13+
- pip
- PostgreSQL (via Supabase)

### Setup

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Configure environment variables in `.env`:
```
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_anon_key
DATABASE_URL=your_database_url
SECRET_KEY=your_secret_key
DEBUG=True
```

3. Run migrations (database schema already created in Supabase):
```bash
python manage.py makemigrations
```

4. Create a superuser:
```bash
python manage.py createsuperuser
```

5. Collect static files:
```bash
python manage.py collectstatic
```

6. Run the development server:
```bash
python manage.py runserver
```

## Database Schema

### Tables
- **user_profiles**: User information and statistics
- **driving_trips**: Individual trip records with metrics
- **eco_tips**: Eco-driving recommendations

### Row Level Security
All tables implement RLS policies to ensure users can only access their own data.

## Eco Score Algorithm

The Eco Score is calculated using the following factors:

1. **Hard Braking Penalty**: -3 points per event (max -20)
2. **Hard Acceleration Penalty**: -3 points per event (max -20)
3. **Idling Time Penalty**: -0.5 points per percentage of trip time idling (max -15)
4. **High Speed Penalty**: -0.3 points for each km/h over 90 km/h (max -20)
5. **Low Speed Penalty**: -0.2 points for average speeds below 30 km/h (max -10)

Starting from 100, penalties are deducted to calculate the final score.

## Mobile Responsive Design

The application is fully responsive with:
- Adaptive layouts for all screen sizes
- Touch-friendly interface elements
- Optimized navigation for mobile devices
- Responsive tables and charts

## Admin Panel

Access the Django admin at `/admin/` to:
- Manage users and profiles
- View and edit trips
- Add or modify eco-driving tips
- Access system logs

## Security Features

- CSRF protection
- Password validation
- SQL injection prevention
- XSS protection
- Secure session management
- Row Level Security (RLS) in database

## Future Enhancements

- Real-time GPS tracking integration
- Mobile app (iOS/Android)
- Social sharing features
- Achievement badges
- Team/group competitions
- Carbon footprint calculator
- Vehicle-specific recommendations
- Route optimization suggestions

## License

MIT License - feel free to use this project for learning and development.

## Support

For issues or questions, please create an issue in the repository.
