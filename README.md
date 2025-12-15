# 🏠 VoyageVilla

![Node.js](https://img.shields.io/badge/Node.js-v22.17.0-green?style=flat&logo=node.js)
![Express](https://img.shields.io/badge/Express-v5.x-lightgrey?style=flat&logo=express)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-green?style=flat&logo=mongodb)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5-purple?style=flat&logo=bootstrap)

> **A fully functional Airbnb clone facilitating property booking and listing management.**

**VoyageVilla** is a full-stack web application that replicates the core functionality of the popular hospitality service, Airbnb. This project demonstrates proficiency in modern web development, specifically the MVC architecture, RESTful routing, and secure authentication flows.

---

## ✨ Key Features

### 🔐 Authentication & Security
* **Robust Auth:** User registration and login using **Passport.js**.
* **Session Management:** Secure sessions stored in MongoDB via `connect-mongo`.
* **Authorization Middleware:**
    * Only authenticated users can create listings/reviews.
    * Only owners can edit/delete their specific listings.

### 🏡 Listing Management
* **CRUD Operations:** Complete Create, Read, Update, and Delete functionality for properties.
* **Rich Content:** Listings include titles, descriptions, prices, dynamic categories (e.g., Mountains, Arctic, Castles), and images hosted on **Cloudinary**.
* **Geo-Location:** Integration with **MapTiler** to display approximate property locations on an interactive map.

### 💬 Reviews & Ratings
* **Interactive Feedback:** Users can leave star ratings (1–5) and text reviews.
* **Smart Deletion:** Deleting a listing automatically cascades and removes associated reviews (Mongoose Middleware).

### 🎨 UI/UX
* **Responsive Design:** Built with **Bootstrap 5** for mobile-first compatibility.
* **Feedback:** Flash messages provide instant success/error notifications.
* **Server-Side Rendering:** Dynamic views rendered using **EJS** and `ejs-mate`.

---

## 🛠️ Tech Stack

| Category | Technologies |
| :--- | :--- |
| **Backend** | Node.js (v22.x), Express.js (v5.x) |
| **Database** | MongoDB, Mongoose, Connect-Mongo |
| **Frontend** | HTML5, CSS3, Bootstrap 5, EJS (Templating), Vanilla JS |
| **Authentication** | Passport, Passport-Local |
| **Cloud Services** | Cloudinary (Image Storage), MapTiler (Maps API) |
| **Validation** | Joi (Server-side schema validation) |

---

## 🚀 Getting Started

Follow the instructions below to set up the project on your local machine.

### Prerequisites
Ensure you have the following installed:
* [Node.js](https://nodejs.org/) (v22.x or higher)
* [MongoDB](https://www.mongodb.com/) (Local or Atlas)
* Accounts for [Cloudinary](https://cloudinary.com/) and [MapTiler](https://www.maptiler.com/)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [ShaileshBakale/VoyageVilla](https://github.com/ShaileshBakale/VoyageVilla.git)
    cd VoyageVilla
    ```

2.  **Install Dependencies:**
    ```bash
    npm install
    ```

3.  **Configure Environment Variables:**
    Create a `.env` file in the root directory and add the following keys:

    ```env
    # Database
    ATLAS_DB_URL=your_mongodb_connection_string

    # Cloudinary (Image Uploads)
    CLOUD_NAME=your_cloudinary_cloud_name
    CLOUD_API_KEY=your_cloudinary_api_key
    CLOUD_API_SECRET=your_cloudinary_api_secret

    # MapTiler (Maps)
    MAPTILER_KEY=your_maptiler_api_key

    # App Secrets
    SECRET=your_session_secret_string
    ```

4.  **Database Initialization (Optional):**
    If you want to seed the database with sample data:
    ```bash
    node init/index.js
    ```

5.  **Run the Application:**
    ```bash
    node app.js
    ```

6.  **Access the App:**
    Open your browser and visit: `http://localhost:8080/listings`

---

## 📂 Architecture Overview

The project adheres to the **MVC (Model-View-Controller)** pattern for scalability and maintainability.

```text
major project/
├── models/            # Mongoose Schemas (Listing, Review, User)
├── views/             # EJS Templates (layouts, includes, listings)
├── controllers/       # Core business logic
├── route/             # Express Routers
├── public/            # Static assets (CSS, JS, Images)
├── init/              # Database seeding scripts
├── utils/             # Error handlers & Wrappers
├── middleware.js      # Auth & Validation middleware
├── schema.js          # Joi Validation schemas
└── app.js             # Entry point
```

---

## 🛤️ API Routes

### Listings (`/listings`)
| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `GET` | `/` | Show all listings | Public |
| `GET` | `/new` | Form to create a new listing | Auth Required |
| `POST` | `/` | Create a new listing | Auth Required |
| `GET` | `/:id` | Show detailed listing info | Public |
| `GET` | `/:id/edit` | Form to edit a listing | Owner Only |
| `PUT` | `/:id` | Update listing details | Owner Only |
| `DELETE` | `/:id` | Delete a listing | Owner Only |

### Reviews (`/listings/:id/reviews`)
| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| `POST` | `/` | Add a review to a listing | Auth Required |
| `DELETE` | `/:reviewId` | Delete a review | Author Only |

### Authentication
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/signup` | Render signup form |
| `POST` | `/signup` | Register new user |
| `GET` | `/login` | Render login form |
| `POST` | `/login` | Authenticate user |
| `GET` | `/logout` | End session |

---

## 🔮 Future Improvements

Here are some features planned for future updates:

- [ ] **Wishlist System:** Allow users to save favorite listings to a private list.
- [ ] **Booking Calendar:** Integrate a real-time calendar to select dates and calculate total cost.
- [ ] **User Profiles:** dedicated dashboard for users to view their booking history and managed listings.
- [ ] **Advanced Filtering:** Filter by price range, amenities (WiFi, AC, Pool), and availability.
- [ ] **Admin Panel:** Dashboard for site administrators to manage users and content moderation.

---

## 👤 Author

**Shailesh Bakale**

* **Repository:** [ShaileshBakale/VoyageVilla](https://github.com/ShaileshBakale/VoyageVilla.git)

---

## 📄 License

This project is licensed under the MIT License.