# 🎓 Smart Campus Collaboration System

> An intelligent platform for fair team formation and seamless project collaboration in campus environments

[![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=flat&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Express.js](https://img.shields.io/badge/Express.js-404D59?style=flat)](https://expressjs.com/)
[![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-43853D?style=flat&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Socket.io](https://img.shields.io/badge/Socket.io-black?style=flat&logo=socket.io&badgeColor=010101)](https://socket.io/)

---

## 📖 Table of Contents
- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Key Features](#-key-features)
- [Architecture](#-architecture)
- [Technology Stack](#-technology-stack)
- [Getting Started](#-getting-started)
- [Applications](#-applications)
- [Intelligent Algorithms](#-intelligent-algorithms)
- [Screenshots](#-screenshots)

---

## 🎯 Overview

**Smart Campus Collaboration System** is a full-stack web application that revolutionizes how students form teams and collaborate on campus projects, hackathons, and research initiatives. It uses AI-powered matching algorithms to ensure fair, skill-based team formation while providing a professional collaboration workspace.

### Why This Platform?

Traditional team formation suffers from:
- 🔄 Same students getting selected repeatedly
- ❌ Skill mismatches in teams
- ⚖️ Lack of equal opportunities
- 🔍 Difficulty finding right teammates
- 📊 No structured collaboration tools

### Our Solution

✅ **AI-Powered Matching** - Intelligent algorithms match students based on skills, experience, and fairness  
✅ **Fair Selection** - Tracks selection frequency to ensure equal opportunities  
✅ **Workload Balancing** - Prevents student burnout by monitoring active projects  
✅ **Professional Workspace** - Complete collaboration suite with chat, tasks, and activity tracking  
✅ **Real-Time Updates** - Instant notifications and live communication  

---

## 🎯 Problem Statement

### Current Challenges in Campus Team Formation

1. **Inequality in Selection**
   - Popular students get selected repeatedly
   - Talented but less-known students miss opportunities
   - Creates exclusive groups and cliques

2. **Skill Mismatches**
   - Teams lack required technical skills
   - No systematic way to assess compatibility
   - Projects fail due to poor team composition

3. **Workload Imbalance**
   - Some students overwhelmed with multiple projects
   - Others struggle to find even one opportunity
   - No visibility into student availability

4. **Poor Collaboration Tools**
   - Reliance on casual messaging apps
   - No centralized project management
   - Difficulty tracking progress and tasks

5. **Lack of Transparency**
   - No clear application process
   - Subjective selection criteria
   - No feedback mechanism

---

## ✨ Key Features

### 🔐 Authentication & Security
- Email/Username registration with verification
- JWT-based secure authentication
- OTP password reset (6-digit, 10-min expiry)
- Protected routes and API endpoints

### 👤 User Profile Management
- Comprehensive profile with skills & proficiency levels
- Work experience tracking
- Interest areas and availability status
- Real-time statistics (projects, selections, ratings)

### 📋 Project Management
- Create projects with detailed requirements
- Define team size, roles, and required skills
- Set deadlines and weekly commitments
- Browse and filter projects by skills/category/role

### 🤖 Intelligent Matching Engine
```
Score = (Skill Match × 40%) + (Experience × 20%) + 
        (Fairness × 20%) + (Workload × 20%)
```
- AI-powered candidate suggestions
- Fair selection algorithm with frequency tracking
- Workload balancing to prevent burnout
- Team combination recommendations

### 📨 Application & Selection
- One-click project applications
- Host review and interview system
- Private interview chat rooms
- Accept/reject with notifications

### 💼 Collaboration Workspace
- **Threaded Chat** - Multiple channels (Backend, Frontend, Design, etc.)
- **Task Board** - Kanban-style with To Do/In Progress/Done
- **Activity Log** - Complete audit trail of all actions
- **Real-Time Sync** - Instant updates via Socket.IO

### 🔔 Smart Notifications
- Application received/status updates
- Project invitations
- Interview requests
- Workspace activities

### 🔍 Search & Discovery
- Advanced filtering (skills, category, role)
- Personalized project recommendations
- User search for invitations

---

## 🏗️ Architecture

### System Architecture Diagram

```
┌──────────────────────────────────────────────────────────────┐
│                  CLIENT LAYER (Port 3000)                    │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐            │
│  │  React UI  │  │   Router   │  │  Tailwind  │            │
│  └─────┬──────┘  └─────┬──────┘  └────────────┘            │
│        │               │                                     │
│  ┌─────▼───────────────▼──────────────────┐                │
│  │      Context API (Auth State)          │                │
│  └─────┬──────────────────────────┬───────┘                │
│        │                          │                         │
│  ┌─────▼────────┐        ┌───────▼────────┐               │
│  │ Axios Client │        │ Socket.IO      │               │
│  │ (HTTP/REST)  │        │ (WebSocket)    │               │
│  └─────┬────────┘        └───────┬────────┘               │
│        │                         │                         │
└────────┼─────────────────────────┼─────────────────────────┘
         │                         │
         │ HTTPS/REST              │ WebSocket
         │                         │
┌────────▼─────────────────────────▼─────────────────────────┐
│                  SERVER LAYER (Port 5000)                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌───────────────────────────────────────────┐             │
│  │          Express.js Server                │             │
│  └────┬──────────────────────────────┬───────┘             │
│       │                              │                     │
│  ┌────▼──────────┐         ┌────────▼────────┐            │
│  │  HTTP Routes  │         │  Socket.IO      │            │
│  │  (REST API)   │         │  Server         │            │
│  └────┬──────────┘         └────────┬────────┘            │
│       │                             │                     │
│  ┌────▼─────────────────────────────▼────────┐            │
│  │          Middleware Layer                 │            │
│  │  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐    │            │
│  │  │ CORS │ │ Auth │ │ JSON │ │Error │    │            │
│  │  └──────┘ └──────┘ └──────┘ └──────┘    │            │
│  └────────────────┬──────────────────────────┘            │
│                   │                                       │
│  ┌────────────────▼──────────────────────────┐           │
│  │          Controllers Layer                │           │
│  │  ┌──────┐ ┌───────┐ ┌──────┐ ┌────────┐ │           │
│  │  │ Auth │ │Project│ │ User │ │Workspace│ │           │
│  │  └──┬───┘ └───┬───┘ └──┬───┘ └───┬────┘ │           │
│  └─────┼─────────┼────────┼─────────┼───────┘           │
│        │         │        │         │                   │
│  ┌─────▼─────────▼────────▼─────────▼───────┐           │
│  │        Business Logic Layer              │           │
│  │  ┌──────────┐ ┌──────┐ ┌──────────┐     │           │
│  │  │ Matching │ │Email │ │Validation│     │           │
│  │  └──────────┘ └──────┘ └──────────┘     │           │
│  └──────────────────┬────────────────────────┘           │
│                     │                                    │
└─────────────────────┼────────────────────────────────────┘
                      │
                      │ Mongoose ODM
                      │
┌─────────────────────▼────────────────────────────────────┐
│              DATABASE LAYER (MongoDB)                    │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  ┌──────────┐ ┌──────────┐ ┌──────────────┐            │
│  │  Users   │ │ Projects │ │Notifications │            │
│  └──────────┘ └──────────┘ └──────────────┘            │
│                                                          │
│  ┌──────────────┐                                       │
│  │InterviewChat │                                       │
│  └──────────────┘                                       │
│                                                          │
└──────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────┐
│                  EXTERNAL SERVICES                       │
├──────────────────────────────────────────────────────────┤
│  ┌──────────┐  ┌──────────┐  ┌──────────┐              │
│  │Nodemailer│  │  MongoDB │  │   JWT    │              │
│  │  (SMTP)  │  │  Atlas   │  │  Auth    │              │
│  └──────────┘  └──────────┘  └──────────┘              │
└──────────────────────────────────────────────────────────┘
```

### Data Flow Architecture

```
┌──────────────────────────────────────────────────────┐
│                  REQUEST FLOW                        │
└──────────────────────────────────────────────────────┘

User Action (Frontend)
    │
    ├─► HTTP Request (REST API)
    │       │
    │       ├─► Express Router
    │       │       │
    │       │       ├─► Auth Middleware (JWT)
    │       │       │       │
    │       │       │       ├─► Controller
    │       │       │       │       │
    │       │       │       │       ├─► Model (Mongoose)
    │       │       │       │       │       │
    │       │       │       │       │       ├─► MongoDB
    │       │       │       │       │       │
    │       │       │       │       │       └─► Response
    │       │       │       │       │
    │       │       │       │       └─► JSON Response
    │       │       │       │
    │       │       │       └─► Error Handler
    │       │       │
    │       │       └─► Response to Client
    │       │
    │       └─► Update UI State
    │
    └─► WebSocket Event (Real-time)
            │
            ├─► Socket.IO Server
            │       │
            │       ├─► Event Handler
            │       │       │
            │       │       ├─► Database Update
            │       │       │
            │       │       └─► Broadcast
            │
            └─► Update UI in Real-time
```

### Component Architecture

```
┌──────────────────────────────────────────────────────┐
│              FRONTEND COMPONENTS                     │
└──────────────────────────────────────────────────────┘

App.js (Root)
    │
    ├─► AuthContext (Global State)
    │       │
    │       └─► user, token, login, logout
    │
    ├─► Router
    │   │
    │   ├─► Public Routes
    │   │   ├─► Login
    │   │   ├─► Signup
    │   │   └─► ForgotPassword
    │   │
    │   └─► Private Routes (Protected)
    │       ├─► Dashboard
    │       │   ├─► Project Cards
    │       │   ├─► Filters
    │       │   └─► Recommendations
    │       │
    │       ├─► Profile
    │       │   ├─► Basic Info
    │       │   ├─► Skills Manager
    │       │   └─► Experience Editor
    │       │
    │       ├─► CreateProject
    │       │   ├─► Project Form
    │       │   ├─► Skills Selector
    │       │   └─► Roles Manager
    │       │
    │       ├─► ProjectDetails
    │       │   ├─► Project Info
    │       │   ├─► Team Members
    │       │   ├─► Applications
    │       │   └─► Suggestions
    │       │
    │       ├─► Workspace
    │       │   ├─► Chat Threads
    │       │   ├─► Task Board
    │       │   └─► Activity Log
    │       │
    │       ├─► MyProjects
    │       ├─► SearchUsers
    │       └─► Notifications
    │
    └─► Global Components
        ├─► Notifications Bell
        └─► Navigation Bar
```

---

## 🛠️ Technology Stack

### Frontend
| Technology | Purpose | Version |
|------------|---------|---------|
| React | UI Framework | 18.x |
| React Router | Navigation | 6.x |
| Tailwind CSS | Styling | 3.x |
| Axios | HTTP Client | 1.x |
| Socket.IO Client | Real-time | 4.x |

### Backend
| Technology | Purpose | Version |
|------------|---------|---------|
| Node.js | Runtime | 14+ |
| Express.js | Web Framework | 4.x |
| MongoDB | Database | 6.x |
| Mongoose | ODM | 8.x |
| Socket.IO | WebSocket | 4.x |
| JWT | Authentication | 9.x |
| bcrypt | Password Hash | 2.x |
| Nodemailer | Email | 6.x |

---

## 🚀 Getting Started

### Prerequisites
```bash
Node.js 14+
MongoDB (local or Atlas)
Gmail account (for emails)
```

### Installation

1. **Clone Repository**
```bash
git clone <repository-url>
cd WEBATHON4
```

2. **Backend Setup**
```bash
cd WEBATHON4/backend
npm install
cp .env.example .env
# Edit .env with your credentials
```

3. **Frontend Setup**
```bash
cd WEBATHON4/frontend
npm install
cp .env.example .env
```

4. **Environment Configuration**

Backend `.env`:
```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/webathon4
JWT_SECRET=<generate-strong-secret>
JWT_EXPIRE=7d
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password
CLIENT_URL=http://localhost:3000
```

Frontend `.env`:
```env
REACT_APP_API_URL=http://localhost:5000/api
```

5. **Seed Database**
```bash
cd backend
node seedUsers.js
```

6. **Run Application**
```bash
# Terminal 1 - Backend
cd backend
npm start

# Terminal 2 - Frontend
cd frontend
npm start
```

7. **Access Application**
- Frontend: http://localhost:3000
- Backend: http://localhost:5000

### Test Credentials
```
Username: user1, Password: user1
Username: user2, Password: user2
... (user1 to user10)
```

---

## 🎯 Applications

### 1. Campus Hackathons
- Students find teammates with complementary skills
- Organizers ensure balanced team formation
- Real-time collaboration during events

### 2. Research Projects
- Faculty post research opportunities
- Students apply based on interests and skills
- Structured workspace for research coordination

### 3. Academic Group Projects
- Course instructors create project requirements
- Students form teams fairly
- Track progress and contributions

### 4. Startup Teams
- Entrepreneurs find co-founders
- Skill-based matching for startup roles
- Professional collaboration environment

### 5. Club Activities
- Campus clubs recruit members for events
- Ensure diverse skill representation
- Manage multiple concurrent projects

### 6. Internship Preparation
- Students form study groups
- Practice interview preparation
- Share resources and experiences

### 7. Competition Teams
- Form teams for coding competitions
- Balance skills across team members
- Coordinate practice sessions

### 8. Social Impact Projects
- NGOs and social organizations post projects
- Students contribute to meaningful causes
- Track impact and outcomes

---

## 🤖 Intelligent Algorithms

### 1. Skill Matching Algorithm
```javascript
skillScore = (matchedSkills / requiredSkills) × 100
proficiencyBonus = avgProficiencyLevel × 0.2
finalSkillScore = skillScore + proficiencyBonus
```

### 2. Fairness Algorithm
```javascript
// Exponential decay based on selection frequency
fairnessScore = Math.exp(-selectionFrequency / 10)

// Examples:
// 0 selections = 1.00 (100% score)
// 5 selections = 0.61 (61% score)
// 10 selections = 0.37 (37% score)
```

### 3. Workload Balancing
```javascript
workloadScore = {
  0: 1.0,  // No active projects
  1: 0.8,  // 1 active project
  2: 0.5,  // 2 active projects
  3+: 0.2  // 3 or more projects
}
```

### 4. Experience Scoring
```javascript
experienceScore = (
  (completedProjects × 0.4) +
  (contributionRating × 0.6)
) / 5
```

### 5. Final Candidate Score
```javascript
totalScore = 
  (skillScore × 0.40) +      // 40% weight
  (experienceScore × 0.20) +  // 20% weight
  (fairnessScore × 0.20) +    // 20% weight
  (workloadScore × 0.20)      // 20% weight
```

### 6. Team Combination Algorithm
```javascript
// Ensures all required skills are covered
// Maximizes team diversity
// Balances experience levels
// Considers availability
```

---

## 📸 Screenshots

### Dashboard
```
┌─────────────────────────────────────────────────────────────┐
│  Smart Campus Collaboration    [🔔] [👤 Profile] [Logout]  │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Filters: [All Skills ▼] [All Categories ▼] [All Roles ▼] │
│                                                              │
│  ┌──────────────────┐  ┌──────────────────┐               │
│  │ Project Card 1   │  │ Project Card 2   │               │
│  │ Title            │  │ Title            │               │
│  │ Description...   │  │ Description...   │               │
│  │ Skills: React... │  │ Skills: Python...│               │
│  │ [Apply]          │  │ [View Details]   │               │
│  └──────────────────┘  └──────────────────┘               │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Workspace
```
┌─────────────────────────────────────────────────────────────┐
│  Project: Smart Campus Platform                             │
├─────────────────────────────────────────────────────────────┤
│  [Chat] [Tasks] [Activity]                                  │
│                                                              │
│  Chat Threads:                                              │
│  ┌────────────┐  ┌─────────────────────────────────────┐  │
│  │ General    │  │ User1: Hey team!                    │  │
│  │ Backend    │  │ User2: Let's discuss the API        │  │
│  │ Frontend   │  │ User3: I'll handle the UI           │  │
│  │ Design     │  │                                      │  │
│  └────────────┘  │ [Type message...]          [Send]   │  │
│                   └─────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

---

## 📊 Project Statistics

- **Total Lines of Code**: ~4,500+
- **API Endpoints**: 25+
- **React Components**: 15+
- **Database Models**: 4
- **Real-time Events**: 10+
- **Documentation Files**: 7

---

## 🔐 Security Features

✅ bcrypt password hashing (12 rounds)  
✅ JWT token authentication  
✅ Email verification required  
✅ OTP-based password reset  
✅ Protected API routes  
✅ Input validation  
✅ CORS configuration  
✅ Environment variable protection  

---

## 🚀 Deployment

### Backend (Render/Railway)
```bash
# Set environment variables
# Deploy from GitHub
# Configure build command: npm install
# Configure start command: npm start
```

### Frontend (Vercel/Netlify)
```bash
# Connect GitHub repository
# Set build command: npm run build
# Set publish directory: build
# Add environment variables
```

### Database (MongoDB Atlas)
```bash
# Create cluster
# Whitelist IP addresses
# Get connection string
# Update MONGODB_URI
```

---

## 📚 Documentation

- [QUICKSTART.md](QUICKSTART.md) - Quick setup guide
- [DEPLOYMENT.md](DEPLOYMENT.md) - Deployment instructions
- [API_DOCUMENTATION.md](API_DOCUMENTATION.md) - API reference
- [SECURITY.md](SECURITY.md) - Security checklist

---

## 🎓 Learning Outcomes

**Technical Skills**: Full-stack development, REST APIs, WebSockets, Database design, Authentication, Algorithms  
**Soft Skills**: Team collaboration, Project management, Problem-solving, Communication  

---

## 🔮 Future Enhancements

- [ ] File upload system
- [ ] Video conferencing
- [ ] Mobile application
- [ ] Advanced analytics
- [ ] Machine learning models
- [ ] Gamification

---

## 🏆 Key Achievements

✅ Complete MERN stack application  
✅ AI-powered matching algorithms  
✅ Real-time collaboration features  
✅ Production-ready deployment  
✅ Comprehensive documentation  
✅ Security best practices  

---

## 📞 Support

For issues and questions:
1. Check documentation files
2. Review API documentation
3. Check console logs
4. Verify environment variables

---

## 📄 License

This project is available for educational and non-commercial use.

---

**Built with ❤️ using React, Node.js, Express, MongoDB, and Socket.IO**

🚀 **Start building better teams today!**
