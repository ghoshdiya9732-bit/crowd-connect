# 🚀 Setup Instructions

Complete guide to set up the Crowd-Connect project locally.

## Prerequisites

- **Node.js** (v18 or higher) - [Download](https://nodejs.org/)
- **MongoDB** (Local or Cloud) - [Setup Guide](https://docs.mongodb.com/manual/installation/)
- **Git** - [Download](https://git-scm.com/)
- **Code Editor** - VS Code recommended

## Step 1: Clone the Repository

```bash
git clone https://github.com/ghoshdiya9732-bit/crowd-connect.git
cd crowd-connect
```

## Step 2: Install Dependencies

```bash
npm install
```

This installs all required packages specified in `package.json`:
- Express.js - Web framework
- MongoDB/Mongoose - Database
- JWT - Authentication
- Multer - File uploads
- And more...

## Step 3: Environment Configuration

1. **Create `.env` file** in the root directory:

```bash
cp .env.example .env
```

2. **Edit `.env`** with your settings:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database Configuration
MONGODB_URI=mongodb://localhost:27017/crowdconnect
# OR use MongoDB Atlas:
# MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/crowdconnect

# Authentication
JWT_SECRET=your_super_secret_jwt_key_here
JWT_EXPIRE=7d

# File Uploads
MAX_FILE_SIZE=5242880
UPLOAD_DIR=./uploads

# Email Configuration (Optional)
EMAIL_SERVICE=gmail
EMAIL_USER=your-email@gmail.com
EMAIL_PASSWORD=your-app-password

# API Configuration
API_URL=http://localhost:5000
CLIENT_URL=http://localhost:3000
```

## Step 4: Database Setup

### Option A: MongoDB Locally

1. **Install MongoDB Community Edition**
   - [Windows](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)
   - [macOS](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-macos/)
   - [Linux](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)

2. **Start MongoDB service**
   ```bash
   # Windows
   net start MongoDB
   
   # macOS
   brew services start mongodb-community
   
   # Linux
   sudo systemctl start mongod
   ```

3. **Verify connection**
   ```bash
   mongosh
   ```

### Option B: MongoDB Atlas (Cloud)

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a free account
3. Create a cluster
4. Get connection string
5. Update `MONGODB_URI` in `.env`

## Step 5: Seed Database (Optional)

Populate the database with sample data:

```bash
npm run seed
```

This will create:
- Sample users
- Sample campaigns
- Sample donations
- FAQ entries

## Step 6: Start Development Server

```bash
npm run dev
```

The server will start with auto-restart on file changes.

**Output:**
```
Server running on http://localhost:5000
Connected to MongoDB
```

## Step 7: Access the Application

- **Frontend:** [http://localhost:5000](http://localhost:5000)
- **Admin Dashboard:** [http://localhost:5000/admin](http://localhost:5000/admin)
- **API Docs:** Check routes in `src/routes/`

## Troubleshooting

### MongoDB Connection Issues

```bash
# Check if MongoDB is running
mongosh

# Check connection string in .env
echo $MONGODB_URI

# Test connection
node -e "const mongoose = require('mongoose'); mongoose.connect(process.env.MONGODB_URI).then(() => console.log('Connected')).catch(err => console.log(err))"
```

### Port Already in Use

```bash
# Windows
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# macOS/Linux
lsof -i :5000
kill -9 <PID>
```

### Dependencies Issues

```bash
# Clear npm cache
npm cache clean --force

# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
```

### Environment Variables Not Loading

1. Ensure `.env` is in the root directory
2. Restart the server after changing `.env`
3. Check for typos in `.env` keys

## Production Deployment

### Deploy to Heroku

```bash
heroku create crowd-connect
heroku config:set MONGODB_URI=your_mongodb_uri
heroku config:set JWT_SECRET=your_secret
git push heroku main
```

### Deploy to Railway/Render

1. Connect your GitHub repository
2. Set environment variables
3. Deploy

## Development Tips

- Use `npm run dev` for development (auto-restart)
- Check logs for errors
- Use MongoDB Compass for database visualization
- Test API with Postman/Insomnia
- Keep `.env` private (never commit)

## Next Steps

- Read [CONTRIBUTING.md](CONTRIBUTING.md) to contribute
- Check [GIT_WORKFLOW.md](GIT_WORKFLOW.md) for Git practices
- Review [README.md](README.md) for project overview

---

Need help? Open an issue on [GitHub Issues](https://github.com/ghoshdiya9732-bit/crowd-connect/issues)
