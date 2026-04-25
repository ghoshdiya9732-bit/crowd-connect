# 🌍 Crowd-Connect

A modern **crowdfunding platform** for social projects. Connect donors with meaningful causes and help bring impactful ideas to life.

## ✨ Features

- 🔐 **User Authentication** - Secure signup, login, and password reset
- 💰 **Campaign Management** - Create and manage fundraising campaigns
- 🎁 **Donations** - Contribute to campaigns with secure payment processing
- 🏷️ **Coupons & Discounts** - Apply promotional codes to donations
- 📋 **FAQ Section** - Frequently asked questions for users
- 💬 **Support Tickets** - Customer support and issue tracking
- 👨‍💼 **Admin Dashboard** - Manage users, campaigns, donations, and messages
- 📱 **Responsive Design** - Works seamlessly on all devices

## 🛠️ Tech Stack

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - ODM for MongoDB
- **JWT** - Authentication
- **bcryptjs** - Password hashing
- **Multer** - File uploads

### Frontend
- **HTML5** - Structure
- **CSS3** - Styling
- **JavaScript (ES6+)** - Interactivity

## 📋 Prerequisites

- Node.js (v18 or higher)
- MongoDB (local or cloud)
- npm or yarn

## 🚀 Installation

1. **Clone the repository**
```bash
git clone https://github.com/ghoshdiya9732-bit/crowd-connect.git
cd crowd-connect
```

2. **Install dependencies**
```bash
npm install
```

3. **Setup environment variables**
Create a `.env` file in the root directory:
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/crowdconnect
JWT_SECRET=your_secret_key_here
NODE_ENV=development
```

4. **Seed the database (optional)**
```bash
npm run seed
```

## 📦 Running the Project

### Development Mode (with auto-restart)
```bash
npm run dev
```

### Production Mode
```bash
npm start
```

The server will run at `http://localhost:5000`

## 📁 Project Structure

```
crowd-connect/
├── public/              # Frontend static files
│   ├── index.html
│   ├── campaigns.html
│   ├── donations.html
│   ├── profile.html
│   ├── admin/          # Admin pages
│   ├── auth/           # Authentication pages
│   ├── css/            # Stylesheets
│   └── js/             # Frontend scripts
├── src/
│   ├── config/         # Database configuration
│   ├── middleware/     # Express middleware
│   ├── models/         # Mongoose schemas
│   ├── routes/         # API routes
│   └── utils/          # Utility functions
├── scripts/            # Database seeding
├── uploads/            # File uploads directory
├── server.js           # Entry point
└── package.json        # Dependencies
```

## 🔌 API Routes

### Authentication
- `POST /api/auth/signup` - Register new user
- `POST /api/auth/login` - User login
- `POST /api/auth/forgot-password` - Reset password

### Campaigns
- `GET /api/campaigns` - Get all campaigns
- `POST /api/campaigns` - Create campaign (admin)
- `GET /api/campaigns/:id` - Get campaign details
- `PUT /api/campaigns/:id` - Update campaign
- `DELETE /api/campaigns/:id` - Delete campaign

### Donations
- `GET /api/donations` - Get all donations
- `POST /api/donations` - Create donation
- `GET /api/donations/user/:userId` - User donations

### Users
- `GET /api/users` - Get all users (admin)
- `GET /api/users/:id` - Get user profile
- `PUT /api/users/:id` - Update profile

### Support
- `POST /api/support/tickets` - Create support ticket
- `GET /api/support/tickets` - Get tickets

## 🔐 Authentication

The platform uses JWT (JSON Web Tokens) for secure authentication:
- Tokens stored in localStorage
- Protected routes require valid token
- Admin routes require admin privileges

## 📄 Database Models

- **User** - User profiles and authentication
- **Campaign** - Fundraising campaigns
- **Donation** - Donation records
- **Coupon** - Discount codes
- **FAQ** - Frequently asked questions
- **SupportTicket** - Customer support tickets

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is open source and available under the MIT License.

## 👥 Contributors

- Diya Ghosh ([@ghoshdiya9732-bit](https://github.com/ghoshdiya9732-bit))
- Prince Singh ([@Prince-ghost](https://github.com/Prince-ghost))

## 📧 Support

For support, reach out via the support ticket system in the application or contact us through GitHub Issues.

---

Made with ❤️ for meaningful causes
