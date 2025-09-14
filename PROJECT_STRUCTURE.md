# Project Structure

```
kadowebtube-automation/
├── src/
│   ├── controllers/           # Route controllers (organized into routes/)
│   ├── database/             # Database configuration and migrations
│   │   ├── connection.js     # Database connection setup
│   │   └── migrate.js        # Migration and seeding scripts
│   ├── middlewares/          # Express middlewares
│   │   ├── auth.js          # Authentication & authorization
│   │   ├── errorHandler.js  # Global error handling
│   │   └── validation.js    # Input validation with Joi
│   ├── models/              # Sequelize models
│   │   ├── index.js         # Model exports
│   │   ├── User.js          # User model
│   │   ├── Campaign.js      # Campaign model  
│   │   ├── Proxy.js         # Proxy model
│   │   ├── GmailAccount.js  # Gmail account model
│   │   └── ActivityLog.js   # Activity logging model
│   ├── routes/              # API route definitions
│   │   ├── auth.js          # Authentication routes
│   │   ├── user.js          # User management routes
│   │   ├── campaigns.js     # Campaign management routes
│   │   ├── proxies.js       # Proxy management routes (admin)
│   │   ├── accounts.js      # Account management routes (admin)
│   │   └── analytics.js     # Analytics and reporting routes
│   ├── services/            # Business logic services
│   │   ├── redis.js         # Redis connection and caching
│   │   ├── queue.js         # Bull queue management
│   │   ├── proxyService.js  # Proxy selection and management
│   │   ├── behaviorService.js # Human behavior simulation
│   │   └── processors/      # Queue job processors
│   │       ├── viewProcessor.js      # YouTube view automation
│   │       ├── likeProcessor.js      # YouTube like automation
│   │       ├── commentProcessor.js   # YouTube comment automation
│   │       ├── subscribeProcessor.js # YouTube subscribe automation
│   │       ├── warmingProcessor.js   # Account warming automation
│   │       └── proxyProcessor.js     # Proxy health checking
│   ├── utils/               # Utility functions
│   │   ├── encryption.js    # Data encryption utilities
│   │   ├── jwt.js          # JWT token utilities
│   │   └── logger.js        # Winston logging setup
│   └── server.js           # Main application entry point
├── tests/                  # Test files
│   ├── setup.js           # Test environment setup
│   └── api.test.js        # API endpoint tests
├── logs/                  # Application logs (created at runtime)
├── docker/                # Docker configuration files
├── docs/                  # Documentation
├── .env.example          # Environment variables template
├── .gitignore           # Git ignore rules
├── .dockerignore        # Docker ignore rules
├── package.json         # Node.js dependencies and scripts
├── ecosystem.config.js  # PM2 process configuration
├── docker-compose.yml   # Docker Compose configuration
├── Dockerfile          # Docker image configuration
└── README.md           # Project documentation
```

## Key Features Implemented

### 🔐 Authentication & Authorization
- JWT-based authentication with refresh tokens
- Role-based access control (user, admin)
- Subscription tier-based permissions
- Secure password hashing with bcrypt
- Input validation and sanitization

### 📊 Campaign Management
- Create, read, update, delete campaigns
- Multiple engagement types (views, likes, comments, subscribes)
- Campaign scheduling and automation
- Real-time progress tracking
- Status management (pending, active, paused, completed)

### 🌐 Proxy Management
- Intelligent proxy rotation algorithms
- Health monitoring and scoring
- Geographic region selection
- Concurrent connection limits
- Automatic failure detection and recovery

### 👥 Account Management
- Gmail account lifecycle management
- 7-stage warming process
- Activity limits and health scoring
- Automatic limitation detection
- Account rotation for campaigns

### 🤖 Behavioral Realism
- Human-like mouse movements and timing
- Realistic viewport and user agent rotation
- Natural interaction patterns
- Variable delays and randomization
- Browser fingerprint management

### 📈 Analytics & Reporting
- Real-time campaign statistics
- Success/failure rate tracking
- Resource utilization monitoring
- Performance analytics
- Data export capabilities (CSV, JSON)

### ⚡ Performance & Scalability
- Redis caching for frequently accessed data
- Bull queue system for task processing
- Database query optimization with indexes
- Connection pooling and resource management
- Horizontal scaling support

### 🔒 Security Features
- AES-256 encryption for sensitive data
- Rate limiting by subscription tier
- CORS and security headers
- Input validation and XSS protection
- SQL injection prevention

## Technology Stack

### Backend Framework
- **Node.js**: Runtime environment
- **Express.js**: Web application framework
- **Sequelize**: PostgreSQL ORM

### Database & Caching  
- **PostgreSQL**: Primary database
- **Redis**: Caching and session storage

### Queue Processing
- **Bull**: Job queue processing
- **Redis**: Queue backend

### Browser Automation
- **Puppeteer**: Headless browser control
- **Puppeteer-extra**: Stealth and anonymization plugins

### Authentication & Security
- **JWT**: Token-based authentication
- **bcrypt**: Password hashing
- **Helmet**: Security headers
- **Joi**: Input validation

### Payment Processing
- **Stripe**: Subscription management

### Monitoring & Logging
- **Winston**: Application logging
- **Custom analytics**: Performance monitoring

## Deployment Options

### Development
```bash
npm run dev
```

### Production (PM2)
```bash
npm run pm2:start
```

### Docker
```bash
docker-compose up -d
```

### Kubernetes
- Scalable container orchestration
- Load balancing and auto-scaling
- Rolling updates and health checks

## API Endpoints Overview

### Authentication
- `POST /api/v1/auth/register` - User registration
- `POST /api/v1/auth/login` - User login
- `POST /api/v1/auth/refresh` - Token refresh
- `POST /api/v1/auth/logout` - User logout

### User Management
- `GET /api/v1/user/profile` - Get user profile
- `PUT /api/v1/user/profile` - Update user profile
- `PUT /api/v1/user/password` - Change password
- `POST /api/v1/user/subscription` - Manage subscription

### Campaign Management
- `POST /api/v1/campaigns` - Create campaign
- `GET /api/v1/campaigns` - List campaigns
- `GET /api/v1/campaigns/:id` - Get campaign details
- `PUT /api/v1/campaigns/:id` - Update campaign
- `DELETE /api/v1/campaigns/:id` - Delete campaign

### Analytics
- `GET /api/v1/analytics/overview` - User analytics overview
- `GET /api/v1/analytics/campaign/:id` - Campaign analytics
- `GET /api/v1/analytics/exports/campaign/:id` - Export data

### Admin Endpoints
- `POST /api/v1/proxies` - Add proxy
- `GET /api/v1/proxies/health` - Proxy health status
- `POST /api/v1/accounts` - Add Gmail account
- `GET /api/v1/accounts/health` - Account health status

## Production Considerations

### Performance
- Enable Redis clustering for high availability
- Use database read replicas for analytics queries
- Implement CDN for static assets
- Monitor and optimize database queries

### Security
- Use HTTPS in production
- Implement proper firewall rules
- Regular security audits and updates
- Monitor for suspicious activity

### Scalability
- Horizontal scaling with load balancers
- Queue worker scaling based on demand
- Database partitioning for large datasets
- Caching optimization

### Monitoring
- Application performance monitoring (APM)
- Error tracking and alerting
- Resource usage monitoring
- Business metrics dashboards

This backend system provides a solid foundation for YouTube automation services while maintaining security, scalability, and reliability standards required for production use.
