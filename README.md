# Short X - AI-Powered Social Entertainment Platform

> An intelligent, scalable full-stack social video platform combining short-form videos, episodic storytelling, and AI-driven content discovery. Built with modern technologies to support millions of users with real-time interactions, intelligent recommendation systems, and seamless creator engagement features.

## 🎬 Project Overview

**Short X** is a production-grade video sharing application that brings together the best of social entertainment with cutting-edge AI/ML capabilities. The platform features:

- **AI-Powered Content Discovery**: Collaborative filtering and machine learning-based recommendation engine
- **Short-Form Videos**: Optimized video player with advanced controls and interactive features
- **Episodic Story Series**: Support for multi-part content narratives
- **Real-Time Interactions**: Socket.IO powered live messaging, notifications, and presence tracking
- **Creator Engagement**: Comprehensive analytics, follower management, and engagement metrics
- **Multi-Platform**: Native iOS/Android apps (React Native) + responsive web platform
- **Enterprise-Scale Infrastructure**: Built on Google Cloud Run, MongoDB, and Cloudinary CDN

---

## 🏗️ Architecture Overview

### Full-Stack Technology Stack

```
┌─────────────────────────────────────────────────────────────┐
│                    FRONTEND LAYER                           │
│  React Native + Expo (iOS, Android) | React Web            │
│  Redux Toolkit | React Navigation | Socket.IO Client       │
└─────────────────────────────────────────────────────────────┘
                           ↓
        ┌──────────────────────────────────────┐
        │      REST API + WebSocket Layer      │
        │    (HTTPS + Socket.IO)               │
        └──────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────────┐
│                    BACKEND LAYER                            │
│  Express.js | MongoDB | Socket.IO Server                   │
│  JWT Auth | Cloudinary Integration | Firebase              │
└─────────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────────┐
│                  INFRASTRUCTURE LAYER                       │
│  Google Cloud Run | MongoDB Atlas | Cloudinary CDN         │
│  Firebase Cloud Messaging | Gmail SMTP                     │
└─────────────────────────────────────────────────────────────┘
```

---

## 📱 Frontend Architecture

### Tech Stack
- **Framework**: React Native v0.73.6 with Expo v50.0.2
- **State Management**: Redux Toolkit v2.5.0
- **Navigation**: React Navigation v6.x
- **HTTP Client**: Axios with JWT interceptors
- **Real-Time**: Socket.IO Client v4.8.1
- **Video Processing**: expo-av, react-native-video, expo-video-thumbnails
- **Media Handling**: expo-image-picker, expo-camera, expo-image-manipulator
- **UI/Animation**: React Native Reanimated, Gesture Handler, Expo Vector Icons
- **Firebase**: Admin SDK for auth, cloud messaging, and analytics
- **Platform Support**: iOS, Android (via Expo), Web (Webpack)

### Project Structure
```
Short X/
├── src/
│   ├── components/              # Reusable UI components
│   │   ├── auth/               # Authentication UI
│   │   ├── creation/           # Video creation flow
│   │   ├── shared/             # Global components
│   │   ├── VideoPlayer.js      # Advanced video playback
│   │   ├── VideoControls.js    # Playback controls
│   │   ├── CommentModal.js     # Comment interaction
│   │   └── VideoOptionsModal.js
│   ├── screens/                # Screen components
│   │   ├── auth/              # Login/signup
│   │   ├── main/              # Feed screens
│   │   ├── creation/          # Video upload/editing
│   │   ├── messaging/         # Chat interface
│   │   ├── profile/           # User profiles
│   │   └── search/            # Search screens
│   ├── services/               # API & external services
│   │   ├── videoService.js
│   │   ├── userService.js
│   │   ├── messageService.js
│   │   ├── uploadService.js
│   │   ├── socketService.js
│   │   ├── firebaseMessagingService.js
│   │   ├── analyticsService.js
│   │   └── notificationService.js
│   ├── store/                  # Redux state management
│   │   ├── index.js
│   │   └── slices/            # Redux slices
│   ├── config/                 # Configuration
│   │   ├── api.js             # Axios instance
│   │   ├── firebase.js        # Firebase setup
│   │   ├── theme.js           # App theme
│   │   ├── constants.js       # App constants
│   │   ├── videoConfig.js     # Video settings
│   │   └── platform.js        # Platform detection
│   ├── contexts/               # React contexts
│   │   └── AuthContext.js     # Auth state
│   ├── navigation/             # Navigation setup
│   │   ├── AppNavigator.js
│   │   ├── AuthNavigator.js
│   │   ├── CreationNavigator.js
│   │   ├── MainTabNavigator.js
│   │   └── LinkingConfiguration.js
│   └── utils/                  # Helper utilities
├── android/                    # Android native code
├── ios/                        # iOS native code
├── app.config.js              # Expo configuration
├── babel.config.js            # Babel setup
├── webpack.config.js          # Web bundler
├── metro.config.js            # React Native bundler
└── package.json               # Dependencies
```

### Key Frontend Features
- **Optimized Video Playback**: Smooth, performant video rendering with lazy loading
- **Gesture Controls**: Swipe for feed navigation, tap for pause/play
- **Authentication Flow**: JWT-based with token refresh and offline support
- **Deep Linking**: Universal links for iOS, deep links for Android, URL scheme on web
- **Network Detection**: NetInfo for graceful offline handling
- **Push Notifications**: Firebase Cloud Messaging integration with foreground/background handlers

---

## 🔙 Backend Architecture

### Tech Stack
- **Framework**: Express.js v4.18.2
- **Database**: MongoDB v8.10.0 with Mongoose ODM
- **Real-Time**: Socket.IO v4.7.4
- **Authentication**: JWT (jsonwebtoken v9.0.2) + bcryptjs
- **Media Storage**: Cloudinary SDK v2.7.0
- **Email Service**: Nodemailer v7.0.11
- **Security**: Helmet v8.0.0, XSS-Clean, MongoSanitize
- **Validation**: express-validator
- **Video Processing**: fluent-ffmpeg
- **Hosting**: Google Cloud Run (asia-south1 region)

### Project Structure
```
backend/
├── app.js                      # Express server & Socket.IO setup
├── config/
│   └── db.js                  # MongoDB connection
├── middleware/
│   ├── auth.js                # JWT verification
│   ├── errorHandler.js        # Error handling
│   ├── validation.js          # Input validation
│   └── videoProcessing.js     # Video upload handling
├── models/                     # MongoDB schemas
│   ├── User.js                # User profiles & social graph
│   ├── Video.js               # Video metadata & engagement
│   ├── Comment.js             # Comments & nested replies
│   ├── Notification.js        # Notification with batching
│   ├── Message.js             # Direct messaging
│   ├── Hashtag.js             # Trending hashtags
│   └── Sound.js               # Audio library
├── routes/                     # API endpoints
│   ├── auth.js                # Authentication (login, register, OTP)
│   ├── videos.js              # Video CRUD & discovery
│   ├── comments.js            # Comment operations
│   ├── users.js               # User profiles & following
│   ├── notifications.js       # Notification delivery
│   ├── messages.js            # Direct messaging
│   ├── discover.js            # Content discovery
│   ├── hashtags.js            # Hashtag operations
│   ├── sounds.js              # Sound library
│   ├── search.js              # Global search
│   └── analytics.js           # Analytics endpoints
├── utils/
│   ├── socketHandlers.js      # WebSocket event handlers
│   ├── firebaseService.js     # Firebase admin operations
│   ├── notificationBatcher.js # Notification aggregation
│   ├── recommendationEngine.js # ML-based feed algorithm
│   ├── abTesting.js           # A/B testing framework
│   └── videoAvailabilityChecker.js
├── scripts/
│   └── updateVideoStatus.js   # Scheduled background tasks
└── package.json               # Dependencies
```

### Database Models

#### User Schema
- **Authentication**: email, password (bcrypt), username
- **Profile**: avatar, displayName, bio, website, location
- **Social**: following[], followers[], likedVideos[], interests[]
- **Engagement**: verified badge, privacySettings
- **Activity**: watchHistory[], lastSeenVideos[], comments[], messages[]

#### Video Schema
- **Content**: videoUrl (Cloudinary), thumbnailUrl, description, duration
- **Metadata**: dimensions, soundId, aspectRatio
- **Engagement**: likes[], likesCount, views, commentsCount, sharesCount
- **Discovery**: hashtags[], mentions[], trendingScore, visibility
- **Processing**: status (processing/published/failed)

#### Notification Schema
- **Types**: like, comment, follow, mention, share, message
- **Batching**: isBatched, batchedSenders[], batchCount, lastBatchUpdate
- **Relations**: recipient, sender, video, comment
- **State**: read timestamp, createdAt

#### Other Models
- **Comment**: Text, author, video, likes, nested replies, timestamps
- **Message**: Direct messaging with read receipts
- **Hashtag**: Text, usage count, trending metrics
- **Sound**: Audio track metadata and references

---

## 🚀 Key Features

### 1. **AI-Powered Recommendation Engine**
- Collaborative filtering for personalized feeds
- Multi-factor scoring:
  - Content matching (keyword similarity)
  - Engagement metrics (likes, comments, shares)
  - Social signals (following relationships)
  - Freshness (recency weighting)
  - Diversity scoring (prevent echo chambers)
- A/B testing framework with 4 variants:
  - Baseline algorithm
  - Enhanced (content-aware)
  - Engagement-focused
  - Discovery-focused
- Deterministic user assignment via hashing

### 2. **Smart Notification System**
- **Notification Batching**: Groups similar actions
  - Example: "Sarah, Mike, and 3 others liked your video"
- **Deduplication**: Prevents spam within 5-second windows
- **Circuit Breaker**: Stops cascade failures
- **Rate Limiting**: Max 100 notifications/minute per user
- **Scheduled Cleanup**: Removes old notifications

### 3. **Real-Time Features**
- Socket.IO with JWT authentication
- User presence tracking (online/offline status)
- Live message delivery with read receipts
- Typing indicators
- Notification real-time push
- Connection pooling and reconnection handling

### 4. **Video Upload & Processing**
- Multer memory storage with Cloudinary streaming
- File size limit: 100MB
- Supported formats: MP4, MOV, WebM, AVI
- Automatic thumbnail generation
- Asynchronous processing with status tracking
- Quality optimization with CDN caching

### 5. **Authentication & Security**
- JWT-based stateless authentication
- OTP-based email verification (Gmail SMTP)
- Password reset flow with token verification
- bcryptjs password hashing (10 salt rounds)
- Token refresh mechanism for web/mobile
- Rate limiting on auth endpoints

### 6. **Content Discovery & Search**
- Global search across videos, users, hashtags, sounds
- Trending hashtags with usage metrics
- User search with follow suggestions
- Hashtag autosuggestion based on trending
- Sound library with preview and search

### 7. **Social Engagement**
- Like/unlike videos with instant updates
- Comment on videos with nested replies
- Follow/unfollow users with follower counts
- Share videos with social integration
- User mentions in videos and comments

### 8. **Creator Analytics**
- View counts per video
- Engagement metrics (likes, comments, shares)
- Follower growth tracking
- Content performance analysis
- Watch time analytics

### 9. **Content Moderation**
- Input validation on all endpoints
- Hashtag limits (max 30 per video)
- Mention limits (max 20 per video)
- Description length validation
- Inappropriate content detection

### 10. **Multi-Platform Support**
- Native iOS app (via Expo)
- Native Android app (via Expo)
- Responsive web application
- Platform-specific optimizations
- Universal deep linking

---

## 📊 API Endpoints

### Authentication
| Method | Endpoint | Purpose |
|--------|----------|---------|
| POST | `/api/auth/register` | User registration with OTP validation |
| POST | `/api/auth/login` | JWT token generation |
| POST | `/api/auth/verify-otp` | Email OTP verification |
| POST | `/api/auth/refresh-token` | Refresh JWT token |
| POST | `/api/auth/forgot-password` | Initiate password reset |
| GET | `/api/auth/me` | Get current user profile |

### Videos
| Method | Endpoint | Purpose |
|--------|----------|---------|
| POST | `/api/videos` | Upload new video |
| GET | `/api/videos` | Get personalized feed |
| GET | `/api/videos/discover` | Get discovery recommendations |
| GET | `/api/videos/:id` | Get video details |
| PUT | `/api/videos/:id` | Update video metadata |
| DELETE | `/api/videos/:id` | Delete video |
| POST | `/api/videos/:id/like` | Like video |
| DELETE | `/api/videos/:id/like` | Unlike video |
| GET | `/api/videos/:id/comments` | Get video comments |

### Comments
| Method | Endpoint | Purpose |
|--------|----------|---------|
| POST | `/api/comments` | Add comment to video |
| GET | `/api/comments/:id` | Get comment details |
| PUT | `/api/comments/:id` | Edit comment |
| DELETE | `/api/comments/:id` | Delete comment |
| POST | `/api/comments/:id/like` | Like comment |

### Users
| Method | Endpoint | Purpose |
|--------|----------|---------|
| GET | `/api/users/:id` | Get user profile |
| PUT | `/api/users/:id` | Update user profile |
| POST | `/api/users/:id/follow` | Follow user |
| DELETE | `/api/users/:id/follow` | Unfollow user |
| GET | `/api/users/:id/followers` | Get followers list |
| GET | `/api/users/:id/following` | Get following list |

### Notifications
| Method | Endpoint | Purpose |
|--------|----------|---------|
| GET | `/api/notifications` | Get batched notifications |
| PUT | `/api/notifications/:id/read` | Mark notification as read |
| DELETE | `/api/notifications/:id` | Delete notification |

### Messaging
| Method | Endpoint | Purpose |
|--------|----------|---------|
| POST | `/api/messages` | Send direct message |
| GET | `/api/messages/:userId` | Get message thread |
| GET | `/api/messages` | Get all conversations |
| PUT | `/api/messages/:id/read` | Mark message as read |

### Discovery
| Method | Endpoint | Purpose |
|--------|----------|---------|
| GET | `/api/hashtags/trending` | Get trending hashtags |
| GET | `/api/hashtags/:tag` | Get videos by hashtag |
| GET | `/api/search` | Global search |
| GET | `/api/sounds` | Get sound library |

### Analytics
| Method | Endpoint | Purpose |
|--------|----------|---------|
| GET | `/api/analytics/videos/:id` | Video analytics |
| GET | `/api/analytics/profile` | Profile analytics |

---

## 🔧 Installation & Setup

### Prerequisites
- **Node.js** >= 16.0.0
- **npm** or **yarn**
- **MongoDB** (local or Atlas)
- **Cloudinary** account for media storage
- **Firebase** project for authentication and messaging
- **Gmail** account for email service

### Backend Setup

```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install

# Create .env file with required variables
cat > .env << EOF
PORT=5000
MONGODB_URI=mongodb+srv://user:password@cluster.mongodb.net/shortx
JWT_SECRET=your_super_secret_key_here
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_PRIVATE_KEY=your_private_key
FIREBASE_CLIENT_EMAIL=your_email@project.iam.gserviceaccount.com
EMAIL_USER=your_gmail@gmail.com
EMAIL_PASSWORD=your_gmail_app_password
FRONTEND_URL=http://localhost:3000
NODE_ENV=development
EOF

# Start development server
npm start

# Server runs on http://localhost:5000
```

### Frontend Setup

```bash
# Navigate to frontend directory
cd "Short X"

# Install dependencies
npm install

# For iOS development
cd ios && pod install && cd ..

# Create .env file (or configure in app.config.js)
# Set API_BASE_URL to your backend URL

# Start Expo development server
npm start

# Options:
# - Press 'i' for iOS simulator
# - Press 'a' for Android emulator
# - Press 'w' for web browser
```

### Firebase Setup

1. Create a Firebase project at https://console.firebase.google.com
2. Enable these services:
   - Authentication (Email/Password, Google)
   - Cloud Messaging (FCM)
   - Analytics
3. Download service account JSON and add to backend
4. Download Google Services JSON for Android app
5. Download GoogleService-Info.plist for iOS app
6. Configure in `src/config/firebase.js`

### Environment Variables

**Backend (.env)**
```env
# Server
PORT=5000
NODE_ENV=development

# Database
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/dbname

# Authentication
JWT_SECRET=your_long_secret_key_minimum_32_characters
JWT_EXPIRE=7d

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Firebase
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_PRIVATE_KEY=-----BEGIN PRIVATE KEY-----\n...
FIREBASE_CLIENT_EMAIL=firebase-adminsdk@project.iam.gserviceaccount.com

# Email Service
EMAIL_USER=your_gmail@gmail.com
EMAIL_PASSWORD=your_gmail_app_password
EMAIL_FROM=noreply@shortx.app

# CORS
FRONTEND_URL=http://localhost:3000

# Socket.IO
SOCKET_CORS_ORIGIN=http://localhost:3000
```

**Frontend (app.config.js)**
```javascript
{
  extra: {
    API_BASE_URL: "http://localhost:5000",
    SOCKET_URL: "http://localhost:5000",
    MAX_VIDEO_SIZE: 104857600, // 100MB
    MAX_VIDEO_DURATION: 60, // 60 seconds
  }
}
```

---

## 🏃 Running the Application

### Development Mode

**Terminal 1 - Backend**
```bash
cd backend
npm start
```

**Terminal 2 - Frontend**
```bash
cd "Short X"
npm start
# Select desired platform (iOS/Android/Web)
```

### Production Build

**Backend**
```bash
cd backend
npm run build      # TypeScript compilation if applicable
npm start          # Start production server
```

**Frontend - Web**
```bash
cd "Short X"
npm run web        # Build web version
# Host the generated build files
```

**Frontend - Mobile**
```bash
cd "Short X"
eas build --platform ios     # Build for iOS
eas build --platform android # Build for Android
```

---

## 🔐 Security Features

- **Helmet.js**: Secure HTTP headers
- **JWT**: Stateless token-based authentication
- **bcryptjs**: Password hashing (10 rounds)
- **MongoSanitize**: NoSQL injection prevention
- **XSS-Clean**: Cross-site scripting prevention
- **CORS**: Restricted to allowed origins
- **Rate Limiting**: Per-endpoint request limiting
- **Input Validation**: express-validator on all routes
- **Cloudinary**: Signed URLs for media uploads
- **HTTPS**: SSL/TLS encryption
- **Token Rotation**: Automatic refresh tokens

---

## 📈 Performance Optimization

- **Video Caching**: CDN via Cloudinary
- **Lazy Loading**: Infinite scroll with pagination
- **Code Splitting**: React code splitting on web
- **Image Optimization**: Automatic quality adjustment
- **Database Indexing**: Indexed queries for speed
- **Compression**: GZIP compression on backend
- **Connection Pooling**: MongoDB connection pooling
- **Worker Threads**: FFmpeg video processing
- **Notification Batching**: Reduced database writes
- **WebSocket Optimization**: Binary encoding for Socket.IO

---

## 📱 Deployment

### Backend Deployment (Google Cloud Run)
```bash
# Build Docker image
docker build -t short-x-backend .

# Push to Google Cloud Registry
gcloud builds submit --tag gcr.io/your-project/short-x-backend

# Deploy to Cloud Run
gcloud run deploy short-x-backend \
  --image gcr.io/your-project/short-x-backend \
  --platform managed \
  --region asia-south1 \
  --set-env-vars "MONGODB_URI=...,JWT_SECRET=..."
```

### Frontend Deployment

**Web**
```bash
npm run web
# Deploy build/ folder to Vercel, Netlify, or GitHub Pages
```

**Mobile**
```bash
eas build --platform all
eas submit
```

---

## 🐛 Troubleshooting

### Backend Connection Issues
```bash
# Check MongoDB connection
mongo "mongodb+srv://user:pass@cluster.mongodb.net/shortx"

# Check Cloudinary credentials
curl "https://api.cloudinary.com/v1_1/YOUR_CLOUD_NAME/resources/video"
```

### Video Upload Failures
- Verify Cloudinary API key and secret
- Check file size (max 100MB)
- Verify supported video format

### Firebase Push Notifications Not Working
- Verify Firebase configuration
- Check FCM token generation on device
- Ensure notification permissions granted

### Socket.IO Connection Issues
- Verify backend and frontend URLs match
- Check CORS configuration
- Verify JWT token in Socket.IO auth

---

## 📚 Documentation

- [Backend API Documentation](./backend/README.md)
- [Frontend Developer Guide](./Short%20X/README.md)
- [Firebase Setup Guide](./Short%20X/FIREBASE_SETUP.md)
- [Video Processing](./backend/middleware/videoProcessing.js)
- [Recommendation Algorithm](./backend/utils/recommendationEngine.js)

---

## 🤝 Contributing

1. Create a feature branch (`git checkout -b feature/AmazingFeature`)
2. Commit changes (`git commit -m 'Add AmazingFeature'`)
3. Push to branch (`git push origin feature/AmazingFeature`)
4. Open a Pull Request

---

## 📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 📞 Support

For support, email support@shortx.app or open an issue on GitHub.

---

## 🙏 Acknowledgments

- Built with React Native and Expo for cross-platform development
- Firebase for authentication and cloud messaging
- Cloudinary for scalable media storage
- MongoDB for flexible data modeling
- Google Cloud Run for serverless deployment

---

## 📊 Project Statistics

| Metric | Value |
|--------|-------|
| **Total Models** | 7 (User, Video, Comment, Notification, Message, Hashtag, Sound) |
| **API Endpoints** | 50+ |
| **Supported Platforms** | 3 (iOS, Android, Web) |
| **Real-time Features** | 5+ (messaging, notifications, presence, typing, updates) |
| **Recommendation Variants** | 4 (A/B testing framework) |
| **Database Collections** | 7 |
| **Authentication Methods** | 2 (JWT, OTP) |
| **Middleware Layers** | 4 (Auth, Validation, Error Handling, Video Processing) |

---

**Last Updated**: June 2026  
**Version**: 1.0.0  
**Status**: Production Ready

---

*Short X - Transforming Social Entertainment* 🚀
