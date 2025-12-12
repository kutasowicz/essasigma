# mObywatel - Polish ID Card Generator

## Overview
Aplikacja do generowania polskich dowodów osobistych (mObywatel) z systemem autentykacji i kontroli dostępu.

**Ważne**: Ta aplikacja nie generuje prawdziwych dokumentów i jest wyłącznie do użytku osobistego.

## Architektura

### Single Flask Application (Port 5000)
- `app.py` - Flask application serving both static files and API endpoints
- Automatically initializes database on startup
- Uses PostgreSQL for persistent storage

### HTML Pages
- `admin-login.html` - Admin panel login (main entry point)
- `login.html` - User login/registration
- `gen.html` - Document generator (requires login)
- `id.html` - Document preview
- `admin.html` - Admin panel (user management)

### API Endpoints
- `POST /api/auth/create-user` - Create new user
- `POST /api/auth/login` - User login
- `POST /api/documents/save` - Save generated document
- `GET /api/documents/<id>` - Get document by ID
- `GET /api/admin/users` - List all users (admin)
- `PUT /api/admin/users/<id>/access` - Toggle user access (admin)
- `GET /api/admin/documents` - List all documents (admin)

### Database Tables
1. `users` - User accounts with access control
2. `generated_documents` - Saved document data (JSON)

## Setup

### Environment Variables
- `DATABASE_URL` - PostgreSQL connection string (auto-configured by Replit)

### Default Admin Account
- Username: `mamba`
- Password: `MangoMango67`

## Workflows
- **Flask App** - `python app.py` (port 5000)

## Deployment
- Target: Autoscale
- Command: `gunicorn --bind=0.0.0.0:5000 --reuse-port app:app`

## Technology Stack
- **Backend**: Flask (Python)
- **Database**: PostgreSQL (Replit Neon)
- **Frontend**: Pure HTML/CSS/JavaScript
- **Package Manager**: uv/pip

## Recent Changes

### December 12, 2025
- Configured for Replit environment
- Set up PostgreSQL database
- Configured Flask workflow on port 5000
- Set up autoscale deployment with gunicorn
