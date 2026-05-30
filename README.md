# ShopEZ - E-commerce Application

A full-stack MERN (MongoDB, Express.js, React.js, Node.js) e-commerce platform providing seamless online shopping experience with secure authentication, comprehensive product catalog, and robust seller dashboard.

## 🌟 Features

### For Customers
- **User Authentication**: Secure JWT-based registration and login
- **Product Browsing**: Comprehensive catalog with search and filtering
- **Shopping Cart**: Add, remove, and manage items
- **Checkout**: Secure payment processing
- **Order Tracking**: View order history and status
- **Reviews & Ratings**: Leave feedback on purchases
- **Wishlist**: Save favorite items

### For Sellers
- **Dashboard**: Real-time analytics and metrics
- **Inventory Management**: Manage products and stock levels
- **Order Management**: View and process customer orders
- **Revenue Reports**: Track sales and earnings
- **Product Analytics**: Insights into product performance

### For Admins
- **User Management**: Manage users and sellers
- **Moderation**: Approve products and sellers
- **System Monitoring**: Track platform activity
- **Content Management**: Manage categories and promotions

## 📋 Prerequisites

- **Node.js** v18+
- **MongoDB** (local or Atlas)
- **npm** or **yarn**
- **Git**

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/24eg105g01-commits/ShopEZ-E-commerce-Application.git
cd ShopEZ-E-commerce-Application
```

### 2. Backend Setup
```bash
cd backend
npm install
```

Create a `.env` file in the backend directory:
```env
PORT=5000
MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/shopez
JWT_SECRET=your_jwt_secret_key_here
JWT_EXPIRE=7d
NODE_ENV=development
CORS_ORIGIN=http://localhost:3000
```

### 3. Frontend Setup
```bash
cd ../frontend
npm install
```

Create a `.env` file in the frontend directory:
```env
REACT_APP_API_URL=http://localhost:5000/api
```

### 4. Run the Application

**Terminal 1 - Backend:**
```bash
cd backend
npm start
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm start
```

The application will be available at `http://localhost:3000`

## 📁 Project Structure

```
ShopEZ-E-commerce-Application/
├── backend/
│   ├── config/
│   │   └── database.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── productController.js
│   │   ├── cartController.js
│   │   ├── orderController.js
│   │   └── userController.js
│   ├── models/
│   │   ├── User.js
│   │   ├── Product.js
│   │   ├── Cart.js
│   │   ├── Order.js
│   │   └── Review.js
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── productRoutes.js
│   │   ├── cartRoutes.js
│   │   ├── orderRoutes.js
│   │   └── userRoutes.js
│   ├── middleware/
│   │   ├── auth.js
│   │   └── errorHandler.js
│   ├── .env
│   ├── .gitignore
│   ├── server.js
│   └── package.json
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.js
│   │   │   ├── Footer.js
│   │   │   ├── ProductCard.js
│   │   │   └── ...
│   │   ├── pages/
│   │   │   ├── Home.js
│   │   │   ├── ProductDetail.js
│   │   │   ├── Cart.js
│   │   │   ├── Checkout.js
│   │   │   ├── Login.js
│   │   │   └── Dashboard.js
│   │   ├── services/
│   │   │   └── api.js
│   │   ├── App.js
│   │   └── index.js
│   ├── .env
│   ├── .gitignore
│   ├── package.json
│   └── README.md
├── .gitignore
└── README.md
```

## 🔐 Security Features

- **JWT Authentication**: Secure token-based authentication
- **Password Encryption**: bcryptjs for secure password hashing
- **CORS Protection**: Cross-origin resource sharing configured
- **Protected Routes**: Role-based access control
- **Input Validation**: Server-side validation for all inputs
- **Error Handling**: Centralized error handling middleware

## 📊 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `POST /api/auth/refresh` - Refresh token

### Products
- `GET /api/products` - Get all products
- `GET /api/products/:id` - Get product details
- `POST /api/products` - Create product (seller only)
- `PUT /api/products/:id` - Update product (seller only)
- `DELETE /api/products/:id` - Delete product (seller only)

### Cart
- `GET /api/cart` - Get user cart
- `POST /api/cart/add` - Add item to cart
- `PUT /api/cart/:itemId` - Update cart item
- `DELETE /api/cart/:itemId` - Remove from cart

### Orders
- `POST /api/orders` - Create order
- `GET /api/orders` - Get user orders
- `GET /api/orders/:id` - Get order details
- `PUT /api/orders/:id` - Update order status (admin only)

### Users
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update profile
- `GET /api/users/:id` - Get user info (admin only)

## 🛠️ Technology Stack

### Backend
- **Express.js**: Web framework
- **MongoDB**: NoSQL database
- **Mongoose**: ODM for MongoDB
- **JWT**: Authentication
- **bcryptjs**: Password encryption
- **CORS**: Cross-origin handling
- **dotenv**: Environment variables

### Frontend
- **React.js**: UI library
- **React Router**: Routing
- **Axios**: HTTP client
- **Bootstrap/Material-UI**: UI framework
- **Redux**: State management (optional)
- **Chart.js**: Data visualization

## 📈 Database Schema

### User Collection
```javascript
{
  _id: ObjectId,
  name: String,
  email: String (unique),
  password: String (hashed),
  phone: String,
  address: Object,
  role: String (CUSTOMER/SELLER/ADMIN),
  avatar: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Product Collection
```javascript
{
  _id: ObjectId,
  name: String,
  description: String,
  price: Number,
  category: String,
  seller: ObjectId (ref: User),
  images: [String],
  stock: Number,
  ratings: Number,
  reviews: [ObjectId],
  createdAt: Date,
  updatedAt: Date
}
```

### Order Collection
```javascript
{
  _id: ObjectId,
  user: ObjectId (ref: User),
  items: [{
    product: ObjectId,
    quantity: Number,
    price: Number
  }],
  totalPrice: Number,
  status: String,
  shippingAddress: Object,
  createdAt: Date,
  updatedAt: Date
}
```

## 🧪 Testing

Run tests using:
```bash
npm test
```

## 📝 Deployment

### Deploy Backend (Heroku/Railway)
```bash
cd backend
npm install -g heroku
heroku login
heroku create shopez-api
git push heroku main
```

### Deploy Frontend (Vercel/Netlify)
```bash
cd frontend
npm run build
# Deploy the build folder to Vercel or Netlify
```

## 🔗 Links

- **[Live Demo](#)** - Coming Soon
- **[GitHub Repository](https://github.com/24eg105g01-commits/ShopEZ-E-commerce-Application)**

## 📞 Support

For issues or questions, please create an issue on GitHub or contact us at support@shopez.com

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Contributors

- **24eg105g01-commits** - Main Developer

---

**Last Updated:** May 30, 2026
