# Food Management & Sustainability Platform

**INNOVATEX Hackathon Project - Part 1**

AI-Powered Food Management supporting **SDG 2: Zero Hunger** and **SDG 12: Responsible Consumption and Production**.

## 📋 Project Overview

A full-stack web application that enables individuals, families, and community groups to manage food consumption, track inventory, reduce waste, and access sustainability resources. The platform combines user-friendly food tracking with rule-based resource recommendations.

## 🛠️ Tech Stack

### Backend
- **Framework**: FastAPI
- **Database**: PostgreSQL (port 5433)
- **ORM**: SQLAlchemy
- **Validation**: Pydantic
- **Authentication**: JWT (python-jose)
- **Password Hashing**: Passlib with bcrypt
- **AI Framework**: LangChain, LangGraph (for Part 2)
- **LLM**: Gemini API (for Part 2)
- **File Storage**: Firebase Admin SDK
- **Package Manager**: uv

### Frontend
- **Framework**: Next.js 16 (React 19)
- **Language**: TypeScript
- **Styling**: Tailwind CSS v4
- **UI Components**: ShadCN UI
- **Form Validation**: Zod + React Hook Form
- **HTTP Client**: Axios
- **Icons**: Lucide React
- **Charts**: Recharts (for future analytics)
- **Package Manager**: pnpm

### DevOps
- **Containerization**: Docker & Docker Compose
- **Database**: PostgreSQL 16.5

## 📁 Project Structure

```
BUBT/
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py              # FastAPI application entry
│   │   ├── config.py            # Environment configuration
│   │   ├── database.py          # Database connection
│   │   ├── models.py            # SQLAlchemy models
│   │   ├── schemas.py           # Pydantic schemas
│   │   ├── auth.py              # Authentication logic
│   │   ├── seed_data.py         # Database seeding
│   │   └── routers/
│   │       ├── auth.py          # Auth endpoints
│   │       ├── users.py         # User management
│   │       ├── food_items.py    # Food items catalog
│   │       ├── inventory.py     # User inventory
│   │       ├── consumption.py   # Consumption logs
│   │       ├── resources.py     # Sustainability resources
│   │       ├── uploads.py       # File uploads
│   │       └── dashboard.py     # Dashboard summary
│   ├── Dockerfile
│   ├── requirements.txt
│   └── .env
├── frontend/
│   ├── src/
│   │   ├── app/
│   │   │   ├── layout.tsx
│   │   │   ├── page.tsx
│   │   │   ├── login/page.tsx
│   │   │   ├── register/page.tsx
│   │   │   ├── dashboard/page.tsx
│   │   │   ├── inventory/page.tsx
│   │   │   ├── logs/page.tsx
│   │   │   ├── resources/page.tsx
│   │   │   └── profile/page.tsx
│   │   ├── components/
│   │   │   ├── ProtectedRoute.tsx
│   │   │   ├── DashboardLayout.tsx
│   │   │   └── ui/              # ShadCN components
│   │   ├── contexts/
│   │   │   └── AuthContext.tsx
│   │   ├── lib/
│   │   │   ├── api.ts
│   │   │   ├── utils.ts
│   │   │   └── validations.ts   # Zod schemas
│   │   └── types/
│   │       └── index.ts
│   ├── Dockerfile
│   ├── package.json
│   ├── components.json
│   └── .env.local
├── docker-compose.yml
├── .gitignore
└── README.md
```

## 🚀 Setup Instructions

### Prerequisites

- Docker & Docker Compose
- Node.js 20+ (for local frontend development)
- pnpm (for frontend)
- Python 3.11+ (for local backend development)
- uv (Python package installer)

### Quick Start with Docker (Recommended)

1. **Clone the repository**
   ```bash
   cd d:\Prog_Stuffs\BUBT
   ```

2. **Configure environment variables**

   Backend (.env already created):
   ```bash
   # Edit backend/.env if needed
   # Update SECRET_KEY for production
   # Add FIREBASE_CONFIG and GEMINI_API_KEY when ready
   ```

   Frontend (.env.local already created):
   ```bash
   # frontend/src/.env.local
   NEXT_PUBLIC_API_URL=http://localhost:8000
   ```

3. **Start all services**
   ```bash
   docker-compose up --build
   ```

   This will start:
   - PostgreSQL on `localhost:5433`
   - Backend API on `http://localhost:8000`
   - Frontend on `http://localhost:3000`

4. **Access the application**
   - Frontend: http://localhost:3000
   - Backend API Docs: http://localhost:8000/docs
   - Backend Health: http://localhost:8000/health

### Local Development Setup

#### Backend Setup

```bash
cd backend

# Install uv if not already installed
curl -LsSf https://astral.sh/uv/install.sh | sh

# Install dependencies
uv pip install -r requirements.txt

# Start PostgreSQL via Docker
docker-compose up postgres

# Run migrations (tables are auto-created on startup)
# Run the application
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

#### Frontend Setup

```bash
cd frontend

# Install pnpm if not already installed
npm install -g pnpm

# Install dependencies
pnpm install

# Install required packages (if not already done)
pnpm add axios react-hook-form @hookform/resolvers date-fns recharts

# Install ShadCN components
npx shadcn@latest add button
npx shadcn@latest add input
npx shadcn@latest add card
npx shadcn@latest add label
npx shadcn@latest add select
npx shadcn@latest add textarea
npx shadcn@latest add table
npx shadcn@latest add dialog

# Run development server
pnpm dev
```

## 📊 Database Schema

### Users
- User authentication and profile data
- Household size, dietary preferences, budget range, location

### Food Items (Seeded Data)
- 20+ common food items
- Categories: fruit, vegetable, dairy, grain, protein
- Expiration periods, cost per unit, units

### User Inventory
- User's current food stock
- Quantity, purchase/expiration dates, notes
- Links to food items catalog

### Consumption Logs
- Daily food usage tracking
- Manual or catalog-based entries
- Category tagging

### Resources (Seeded Data)
- 20+ sustainability tips and guides
- Categories: waste reduction, storage, budget tips, nutrition, meal planning
- Types: article, video, guide

### Uploads
- Receipt/label image uploads
- Firebase storage URLs
- Association with inventory/logs

## ✨ Part 1 Features Implemented

### 1. Authentication & User Management ✅
- User registration with email/password
- Secure login with JWT tokens
- Password hashing with bcrypt
- Form validation (Zod frontend, Pydantic backend)
- User profile management

### 2. User Profile & Consumption Logging ✅
- Editable user profiles
- Manual food consumption logging
- Inventory management (add/remove items)
- Consumption history tracking

### 3. Food Items Database ✅
- 20 pre-seeded food items
- Categories: fruit, vegetable, dairy, grain, protein
- Expiration periods and cost data
- Searchable and filterable

### 4. Resources Database ✅
- 20 pre-seeded sustainability resources
- Categories: waste reduction, storage, budget tips, nutrition
- Filterable by category
- External links to articles/videos

### 5. Basic Tracking Logic ✅
- Inventory summaries
- Recent consumption logs
- Items expiring soon (within 7 days)
- Rule-based resource recommendations matching:
  - User's consumption categories
  - Dietary preferences
  - Budget range

### 6. Image Upload Interface ✅
- Upload UI for receipts/labels
- JPG/PNG support
- Manual association with inventory/logs
- Firebase storage ready (placeholder in Part 1)

### 7. User Dashboard ✅
- Quick inventory and log summaries
- Expiring items alerts
- Recent consumption history
- Personalized resource recommendations with reasoning

### 8. Clean, Responsive UI ✅
- TailwindCSS styling
- ShadCN UI components
- Mobile-responsive design
- Clear navigation (Dashboard, Inventory, Logs, Resources, Profile)
- Accessibility considerations

## 🔌 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### Users
- `GET /api/users/me` - Get current user profile
- `PUT /api/users/me` - Update user profile

### Food Items
- `GET /api/food-items` - List all food items
- `GET /api/food-items/{id}` - Get food item details
- `GET /api/food-items/categories/list` - Get categories

### Inventory
- `GET /api/inventory` - Get user inventory
- `POST /api/inventory` - Add inventory item
- `PUT /api/inventory/{id}` - Update inventory item
- `DELETE /api/inventory/{id}` - Delete inventory item

### Consumption Logs
- `GET /api/consumption` - Get consumption logs
- `POST /api/consumption` - Add consumption log
- `DELETE /api/consumption/{id}` - Delete log

### Resources
- `GET /api/resources` - List resources (with filters)
- `GET /api/resources/{id}` - Get resource details
- `GET /api/resources/categories/list` - Get categories

### Dashboard
- `GET /api/dashboard` - Get dashboard summary

### Uploads
- `POST /api/uploads` - Upload file
- `GET /api/uploads` - List user uploads
- `DELETE /api/uploads/{id}` - Delete upload

## 🧪 Testing the Application

1. **Register a new account** at `/register`
2. **Login** at `/login`
3. **Add inventory items** from the pre-seeded food catalog
4. **Log consumption** of food items
5. **View dashboard** to see:
   - Total inventory count
   - Consumption logs count
   - Items expiring soon
   - Recommended resources based on your activity
6. **Browse resources** filtered by category
7. **Update profile** with dietary preferences and budget range

## 🔐 Security Features

- Password hashing with bcrypt
- JWT token-based authentication
- HTTP-only token storage (localStorage for Part 1)
- Input validation on both frontend (Zod) and backend (Pydantic)
- SQL injection protection via SQLAlchemy ORM
- CORS configuration

## 📝 Code Quality

- Type-safe TypeScript frontend
- Pydantic models for backend validation
- Modular router structure
- Separation of concerns (models, schemas, routes)
- Clean code organization
- Reusable UI components

## 🚧 Part 2 Preparation

The architecture is designed to easily integrate:
- AI-powered food scanning (image recognition)
- Smart expiration predictions
- Meal planning with LangChain/LangGraph
- Gemini API for conversational features
- Advanced analytics and visualizations

## 📦 Seed Data

The application comes pre-loaded with:
- **20 Food Items**: Common household foods across all categories
- **20 Resources**: Sustainability tips, storage guides, nutrition advice

## 🐛 Troubleshooting

### Port Conflicts
If port 5433 is in use:
```bash
# Edit docker-compose.yml
ports:
  - "5434:5432"  # Change to available port

# Update backend/.env
DATABASE_URL=postgresql://fooduser:foodpass123@localhost:5434/food_management
```

### Frontend Not Loading
```bash
cd frontend
pnpm install
pnpm dev
```

### Backend Errors
```bash
cd backend
docker-compose logs backend
```

### Database Connection Issues
```bash
docker-compose down
docker-compose up postgres
# Wait for PostgreSQL to be ready
docker-compose up backend frontend
```

## 📄 License

This project is for the INNOVATEX Hackathon.

## 👥 Team

BUBT Hackathon Team

## 📞 Support

For issues or questions, please check:
1. Docker logs: `docker-compose logs`
2. API documentation: `http://localhost:8000/docs`
3. Environment variables configuration

---

**Ready for Part 2!** 🚀

This implementation provides a solid foundation with clean architecture, allowing seamless integration of AI features (LangChain, LangGraph, Gemini API) during the onsite hackathon phase.
