# AI CareerGuide — AI-Based Student Career Guidance System

![AI CareerGuide](https://img.shields.io/badge/AI-CareerGuide-indigo.svg)
![FAI Project](https://img.shields.io/badge/Academic-FAI%20Mini--Project-teal.svg)
![Status](https://img.shields.io/badge/Status-Fully%20Functional-brightgreen.svg)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

> **"Discover Your Strengths. Explore Your Future."**

**AI CareerGuide** is a modern, responsive, full-stack web application developed as a **Fundamentals of Artificial Intelligence (FAI)** academic mini-project. It assists students in discovering personalized, high-compatibility career avenues based on their individual interests, technical and soft skills, academic strengths, personality/working styles, and career goals.

---

## 🌟 Key Demonstration Features

1. **Student Profiling & Auth**: Secure student & administrator authentication using hashed passwords (bcrypt) and JSON Web Tokens (JWT).
2. **Interactive 30-Question Assessment**: Multi-step interactive flow with progress indicators, real-time auto-saving, and diverse response controls (single choice, multi-choice tags, 1–5 competency rating sliders).
3. **Multi-Factor Weighted AI Recommendation Engine**:
   $$\text{Career Score} = (\text{Interests} \times 30\%) + (\text{Skills} \times 25\%) + (\text{Academics} \times 15\%) + (\text{Work Style} \times 15\%) + (\text{Goals} \times 15\%)$$
4. **Explainable AI (XAI) Justifications**:
   - Transparent, auditable breakdown of **"Why this career matches you"** with verified factors.
   - Identified **"Key matching skills"** and **"Skills to improve / Areas to develop"**.
   - Responsible AI framing providing positive guidance rather than deterministic predictions.
5. **Interactive Competency Radar Visualization**: 6-dimensional radar/spider chart analyzing:
   - Analytical Skills
   - Creativity
   - Communication
   - Leadership
   - Technical Aptitude
   - Research & Inquiry
6. **20+ Comprehensive Career Catalog**: Detailed profiles across Technology, Business, Finance, Healthcare, Design, Science, Education, and Media.
7. **Step-by-Step 4-Phase Career Roadmaps**: Actionable progression from foundational learning to industry entry with curated courses (Coursera, edX, Harvard).
8. **Personalized Skill-Gap Analysis**: Dynamic comparison highlighting *"Skills You Have"* vs. *"Skills You Should Improve"* for any target role.
9. **Assessment History & Evolution Tracking**: Compare compatibility changes across multiple assessment runs over time.
10. **Context-Aware AI Chat Assistant**: Floating AI counselor that answers student questions about roles, tools, and learning paths with instant domain intelligence.
11. **Administrative Control Panel**: Comprehensive metrics, real-time analytics charts, complete career CRUD, question management, and student directory.

---

## 🛠️ Technology Stack

| Layer | Technologies Used |
|---|---|
| **Frontend** | React 18, TypeScript, Tailwind CSS, Lucide React, SVG Charts, Vite 5 |
| **Backend** | Python 3.10+, FastAPI, Starlette, Pydantic v2, Uvicorn |
| **Database** | SQLite (Production-ready SQLAlchemy 2.0 ORM, easily extensible to PostgreSQL) |
| **Security** | Bcrypt password hashing, PyJWT authentication, OAuth2 Bearer scheme |
| **AI / Logic** | Lightweight Explainable AI (XAI) weighted recommendation engine |

---

## 🚀 Quick Start Guide

### 1. Prerequisites
- **Python**: Version 3.10 or higher installed
- **Node.js**: Version 18.0 or higher installed (`node -v` and `npm -v`)

### 2. Backend Setup & Run

Open a terminal and navigate to the project directory:

```bash
# Navigate to backend
cd backend

# Install dependencies
python -m pip install fastapi uvicorn sqlalchemy pyjwt bcrypt python-multipart email-validator

# Initialize and seed database (Admin, Student, 20 Careers, 30 Questions)
python -m app.database.seed

# Start the FastAPI backend server
python -m uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
```

The backend API will be live at:
- **API Base**: `http://127.0.0.1:8000/api`
- **Interactive Swagger Docs**: `http://127.0.0.1:8000/docs`
- **ReDoc Documentation**: `http://127.0.0.1:8000/redoc`

---

### 3. Frontend Setup & Run

In a second terminal window, navigate to the `frontend` folder:

```bash
# Navigate to frontend
cd frontend

# Install npm dependencies
npm install

# Start the Vite development server
npm run dev
```

Open your browser and navigate to:
**`http://localhost:5173/`**

---

## 🔑 Demo Credentials (For Evaluation & Viva)

The database comes pre-seeded with ready-to-test accounts:

| Role | Email | Password | Access Level |
|---|---|---|---|
| **Demo Student** | `student@careerguide.com` | `student123` | Full student dashboard, completed assessment, AI results, career roadmaps |
| **System Admin** | `admin@careerguide.com` | `admin123` | Admin dashboard, charts, career CRUD, question manager, student list |

> 💡 **Viva Tip**: On the Login screen, click the **"Demo Student"** or **"Demo Admin"** quick-fill button for immediate 1-click demonstration!

---

## 🧮 AI Recommendation Methodology

The core AI engine uses a normalized, explainable multi-factor scoring algorithm:

```
Career Compatibility Score = 
  (Interest Match × 0.30) + 
  (Skill Match × 0.25) + 
  (Academic Match × 0.15) + 
  (Work Style Match × 0.15) + 
  (Career Goal Match × 0.15)
```

1. **Interest Match (30%)**: Jaccard similarity and semantic matching between student's chosen activities, subjects, and real-world interests against the career's recommended domains.
2. **Skill Match (25%)**: Evaluation of student's self-ratings (1–5) on the career's required core competencies.
3. **Academic Match (15%)**: Alignment of academic stream (Science, Commerce, Arts, etc.) and subject strengths (Math, CS, Biology, etc.) with role prerequisites.
4. **Work Preference Match (15%)**: Compatibility with problem-solving approach (e.g. step-by-step analytical vs. creative exploration) and preferred work environments.
5. **Career Goal Match (15%)**: Alignment with long-term ambitions (technical depth, leadership, entrepreneurship, social impact).

### Ethical AI Principles
- Recommendations are labeled as **actionable guidance**, never as deterministic life predictions.
- No sensitive or exclusionary personal attributes are factored into scoring.
- Every score is accompanied by understandable justification points and concrete learning resources.

---

## 📁 Project Directory Structure

```
LastMiniProject68/
├── backend/
│   ├── app/
│   │   ├── auth/              # JWT & Bcrypt security helpers
│   │   ├── database/          # SQLite / SQLAlchemy connection & seeding
│   │   ├── models/            # Database schema models (User, Career, etc.)
│   │   ├── routes/            # REST API endpoints (auth, student, assessment, etc.)
│   │   ├── schemas/           # Pydantic validation schemas
│   │   ├── services/          # Explainable AI engine & Chat service
│   │   └── main.py            # FastAPI entrypoint & CORS middleware
│   ├── seed_data/             # 20+ careers and 30 assessment questions
│   └── careerguide.db         # SQLite persistent database
├── frontend/
│   ├── src/
│   │   ├── components/        # Navbar, Footer, RadarChart, AIChatbot, CareerCard
│   │   ├── context/           # React AuthContext
│   │   ├── pages/             # 11 full application pages
│   │   ├── services/          # Centralized API client
│   │   └── types/             # TypeScript interfaces
│   ├── tailwind.config.js     # Brand design palette
│   └── vite.config.ts         # Vite bundler configuration
├── docs/                      # Technical architecture documentation
├── .env.example               # Environment variable templates
└── README.md                  # Comprehensive project guide
```

---

## 🔮 Future Enhancements
- Integration with external LLM APIs (OpenAI / Claude / Gemini) for personalized interview preparation simulations.
- Direct resume parsing (PDF) to auto-extract student skills and project experiences.
- Live job market integration (LinkedIn / Indeed API) to show active local internships.

---

**Developed for the FAI Mini-Project Evaluation.**
AI CareerGuide • Empowering Students Through Explainable Artificial Intelligence.
