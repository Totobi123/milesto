# Miles - Security-First Web Application

## Overview

Miles is a security-focused web application designed with advanced protection mechanisms against code inspection, debugging, and unauthorized access. The application features a modern dark-themed UI with red accent colors and implements comprehensive client-side security measures to prevent users from accessing developer tools, viewing source code, or performing unauthorized actions.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Single-Page Application (SPA) Design**
- Static HTML/CSS/JavaScript architecture for simplicity and performance
- No complex frontend frameworks to maintain minimal attack surface
- Responsive design optimized for both desktop and mobile devices with special focus on Android Chrome compatibility

**Security-First Design Pattern**
- Comprehensive keyboard shortcut blocking system preventing access to developer tools (F12, Ctrl+Shift+I, etc.)
- Right-click context menu disabled with event capture and propagation stopping
- Advanced event handling with multiple layers of protection including blur effects and notifications
- Content Security Policy (CSP) headers implemented to prevent XSS attacks

**Mobile-Optimized Experience**
- Extensive viewport and mobile web app meta tags for native-like experience
- Android Chrome theme customization with branded colors
- iOS Safari compatibility with status bar styling
- Touch interaction optimizations with tap highlight removal

### Backend Architecture

**Netlify Serverless Functions**
- Express.js backend converted to serverless functions using serverless-http
- API endpoints for crypto balance checking, bank account verification, and bank listings
- Environment variable support for secure API key management (Etherscan, Flutterwave)
- Automatic scaling and zero server maintenance with Netlify Functions

**Production-Ready Configuration**
- Configured for Netlify deployment with optimal file structure
- Static site hosting from `site/` directory with serverless functions in `netlify/functions/`
- Security headers and CORS properly configured for production environment
- API routing through Netlify redirects for seamless frontend-backend integration

### Security Implementation

**Client-Side Protection Layers**
- Multi-tiered keyboard event blocking with comprehensive key combination detection
- Context menu prevention with immediate feedback system
- Page blur effects and notification system for security violations
- Prevention of common debugging and inspection techniques

**HTTP Security Headers**
- Content Security Policy (CSP) restricting script sources
- X-Frame-Options set to DENY preventing iframe embedding
- X-Content-Type-Options for MIME type sniffing prevention
- Strict Transport Security (HSTS) for HTTPS enforcement
- Cache-Control headers preventing sensitive data caching

**Anti-Debugging Measures**
- Function key blocking (F12, F5-F11)
- Developer tool shortcut prevention
- Print and save functionality disabled
- Tab switching and window management restrictions

## External Dependencies

### Runtime Dependencies
- **Node.js**: Backend serverless function runtime environment
- **Modern Web Browser**: Client-side execution environment with JavaScript ES6+ support

### Development Environment
- **Replit Platform**: Cloud-based development and hosting environment
- **Netlify Platform**: Production hosting for static site and serverless functions

### Browser API Dependencies
- **DOM API**: Event handling, element manipulation, and page interaction
- **Web API**: Keyboard events, context menu control, and viewport management
- **CSS3**: Advanced styling features including backdrop-filter and CSS custom properties

### Security Framework
- **Content Security Policy (CSP)**: Browser-native security policy enforcement
- **HTTP Security Headers**: Browser security feature activation through meta tags
- **Event Capture API**: Advanced DOM event handling for security event prevention

### Mobile Platform Integration
- **Progressive Web App (PWA) APIs**: Mobile app-like experience through web standards
- **Android Chrome**: Custom theme and app integration features
- **iOS Safari**: Mobile web app capabilities and status bar customization

## Project Structure (Deployment-Ready)

```
Miles/
├── site/                    # Frontend files (deployed to Netlify CDN)
│   ├── index.html          # Main application file
│   ├── style.css           # Application styles
│   ├── script.js           # Client-side functionality
│   └── logo.png            # Application logo
├── netlify/                # Backend serverless functions
│   └── functions/          
│       └── api.js          # Express app converted to serverless function
├── netlify.toml            # Netlify deployment configuration
├── package.json            # Node.js dependencies
├── package-lock.json       # Dependency lock file
├── NETLIFY_ENV_SETUP.md    # Environment variables setup guide
└── replit.md              # Project documentation
```

### External API Dependencies
- **Etherscan API**: For crypto wallet balance checking (Ethereum and BNB Smart Chain)
- **Flutterwave API**: For Nigerian bank account verification and bank listings
- Environment variables required: `ETHERSCAN_API_KEY`, `FLUTTERWAVE_SECRET_KEY`
- Fallback fintech verification system for when primary services are unavailable