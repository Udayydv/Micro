# MicroCourses - Mini LMS (MERN MVP)

A mini Learning Management System built with the MERN stack, supporting three user roles: Learner, Creator, and Admin.

## 🎯 Features

### User Roles & Permissions
- **Learner**: Browse and enroll in published courses, view lessons with transcripts, track progress, and earn certificates
- **Creator**: Apply to become a creator, create and manage courses and lessons (after approval)
- **Admin**: Approve creator applications, review & publish courses, manage platform content

### Core Features
- ✅ JWT-based Authentication with role-based access control
- ✅ Course creation and management with video uploads
- ✅ Lesson management with unique ordering
- ✅ Enrollment and progress tracking
- ✅ Certificate generation with unique SHA256 hashes
- ✅ Admin review workflow for courses and creators
- ✅ Responsive UI with Tailwind CSS

## 🚀 Quick Start

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or cloud)
- npm or yarn

### Installation

1. **Clone and install dependencies:**
```bash
git clone <repository-url>
cd microcourses-lms
npm run install-all
```

2. **Set up environment variables:**
Create `backend/.env` file:
```env
MONGODB_URI=mongodb://localhost:27017/microcourses
JWT_SECRET=your_jwt_secret_key_here
PORT=5000
```

3. **Start the development servers:**
```bash
npm run dev
```

This will start:
- Backend server on http://localhost:5000
- Frontend development server on http://localhost:3000

## 📁 Project Structure

```
microcourses-lms/
├── backend/
│   ├── models/          # MongoDB models
│   ├── routes/          # API routes
│   ├── middleware/      # Auth middleware
│   ├── uploads/         # File uploads
│   └── server.js        # Express server
├── frontend/
│   ├── src/
│   │   ├── components/  # React components
│   │   ├── pages/       # Page components
│   │   ├── contexts/    # React contexts
│   │   └── App.jsx      # Main app component
│   └── public/          # Static assets
└── package.json         # Root package.json
```

## 🔧 API Endpoints

### Authentication
- `POST /api/auth/signup` - Register user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user

### Creator Workflow
- `POST /api/creator/apply` - Apply to be a creator
- `GET /api/admin/creators` - List pending applications (admin only)
- `PATCH /api/admin/creator/:id/approve` - Approve creator (admin only)

### Courses & Lessons
- `POST /api/courses` - Create course (creator only)
- `GET /api/courses` - List published courses
- `GET /api/courses/:id` - Course details
- `PATCH /api/courses/:id/publish` - Publish course (admin only)
- `POST /api/lessons` - Add lesson to course
- `GET /api/lessons/:lessonId` - Fetch lesson content

### Enrollment & Progress
- `POST /api/enroll/:courseId` - Enroll in course
- `GET /api/progress` - Get learner's progress
- `PATCH /api/progress/:lessonId/complete` - Mark lesson complete

### Certificates
- `POST /api/certificates/:courseId` - Generate certificate
- `GET /api/certificates/verify/:serialHash` - Verify certificate

## 🧪 MVP Flow (Test Cases)

1. **Creator applies** via `/creator/apply`
2. **Admin approves** the creator via `/admin/creator/:id/approve`
3. **Creator creates** course & lessons (unique order)
4. **Admin reviews** & publishes the course
5. **Learner enrolls** in the published course
6. **Learner completes** all lessons (progress = 100%)
7. **System generates** certificate with unique serial hash

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | React + Vite + Tailwind CSS + React Router |
| Backend | Node.js + Express.js |
| Database | MongoDB + Mongoose ORM |
| Auth | JWT + bcrypt |
| File Upload | Multer |
| Certificate Hash | Node crypto library (SHA256) |

## 📝 Business Rules

- Only published courses are visible to learners
- Lessons within a course must have unique orderIndex
- Certificates are issued only when progress = 100%
- Creator applications require Admin approval
- All courses go through admin review before publication

## 🔒 Security Features

- JWT-based authentication
- Password hashing with bcrypt
- Role-based access control
- File upload validation
- Input validation with express-validator

## 🎨 UI/UX Features

- Responsive design with Tailwind CSS
- Modern, clean interface
- Role-based navigation
- Progress tracking visualization
- Toast notifications
- Loading states and error handling

## 📦 Available Scripts

```bash
# Install all dependencies
npm run install-all

# Start both frontend and backend
npm run dev

# Start only backend
npm run server

# Start only frontend
npm run client
```

## 🚀 Deployment

1. Set up MongoDB (local or cloud like MongoDB Atlas)
2. Configure environment variables
3. Build frontend: `cd frontend && npm run build`
4. Start backend: `cd backend && npm start`

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.
