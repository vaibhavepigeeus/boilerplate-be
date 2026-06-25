# Boilerplate Backend

Django REST API boilerplate extracted from CMT project with the following modules:

- **Login / SSO** — Knox token auth + Azure AD OAuth (`/api/users/`)
- **Forgot password** — OTP + password reset flows
- **User management** — CRUD, activation/deactivation, export
- **Roles** — `UserPermissions` with JSON module permissions
- **Workflow** — Work steps, workflows, instances, dashboard (`/api/workflow/`)
- **Document repository** — Upload/list/view documents (`/api/documents/`)
- **File management** — Centralized file registry (`/api/filemanagement/`)
- **Notifications** — DB + WebSocket (`ws://host/ws/notifications/`)
- **Email** — SMTP utilities + IMAP read/reply
- **Audit** — API request audit, field-level audit, workflow audit (`/api/audit/`)

## Setup

```bash
cd D:\DEP\Kumar\boilerplate\BE
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
copy .env.example .env
# Edit .env with your database and service credentials

python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser
```

## Run

```bash
# HTTP API
python manage.py runserver

# WebSocket notifications (requires Redis)
daphne -b 0.0.0.0 -p 8000 boilerplate.asgi:application
```

## API Routes

| Module | Base URL |
|--------|----------|
| Users / Auth | `/api/users/` |
| Documents | `/api/documents/` |
| File Management | `/api/filemanagement/` |
| Workflow | `/api/workflow/` |
| Audit | `/api/audit/` |

## Infrastructure

- PostgreSQL
- Redis (for Django Channels notifications)
- SMTP server (email)
- AWS S3 (optional, for document/file storage)
- Azure AD app registration (optional, for SSO)
"# boilerplate-be" 
