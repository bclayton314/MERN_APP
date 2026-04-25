# MERN Places App

A full-stack MERN (MongoDB, Express, React, Node.js) application for sharing and managing places/locations. Users can sign up, create places with addresses, and manage their own places.

## Tech Stack

| Layer | Technology |
|-------|------------|
| **Frontend** | React 16.11, React Router DOM 5.1 |
| **Backend** | Express 4.21, Node.js |
| **Database** | MongoDB with Mongoose ODM |
| **Authentication** | JWT-based (custom implementation) |

---

## Project Structure

```
MERN_APP/
├── backend/
│   ├── app.js              # Express server entry point
│   ├── package.json
│   ├── controllers/
│   │   ├── places-controllers.js
│   │   └── users-controllers.js
│   ├── models/
│   │   ├── http-error.js   # Custom error class
│   │   ├── place.js        # Mongoose Place model
│   │   └── user.js         # Mongoose User model
│   ├── routes/
│   │   ├── places-routes.js
│   │   └── users-routes.js
│   └── util/
│       └── location.js     # Geocoding utility
│
└── frontend/
    ├── package.json
    ├── public/
    └── src/
        ├── App.js
        ├── index.js
        ├── index.css
        ├── places/
        │   ├── components/
        │   │   ├── PlaceItem.js/css
        │   │   └── PlaceList.js/css
        │   └── pages/
        │       ├── NewPlace.js
        │       ├── UpdatePlace.js
        │       ├── UserPlaces.js
        │       └── PlaceForm.css
        ├── shared/
        │   ├── components/
        │   │   ├── FormElements/   # Button, Input
        │   │   ├── Navigation/     # MainNavigation, NavLinks, SideDrawer
        │   │   └── UIElements/     # Modal, Card, LoadingSpinner, Map, Avatar
        │   ├── context/
        │   │   └── auth-context.js
        │   ├── hooks/
        │   │   ├── form-hook.js
        │   │   └── http-hook.js
        │   └── util/
        │       └── validators.js
        └── user/
            ├── components/
            │   ├── UserItem.js/css
            │   └── UsersList.js/css
            └── pages/
                ├── Auth.js/css
                └── Users.js
```

---

## Features

### Backend API

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/places` | POST | Create a new place |
| `/api/places/:pid` | GET | Get place by ID |
| `/api/places/user/:uid` | GET | Get all places by user |
| `/api/places/:pid` | PATCH | Update a place |
| `/api/places/:pid` | DELETE | Delete a place |
| `/api/users` | GET | Get all users |
| `/api/users/signup` | POST | User registration |
| `/api/users/login` | POST | User login |

### Frontend Pages

- **Users** (`/`) — Browse all users
- **User Places** (`/:userId/places`) — View places created by a user
- **New Place** (`/places/new`) — Create a new place (authenticated)
- **Update Place** (`/places/:placeId`) — Edit an existing place
- **Auth** (`/auth`) — Login/Signup page

---

## Getting Started

### Prerequisites

- Node.js (v14+ recommended)
- MongoDB (local or Atlas cloud instance)

### Installation

1. **Clone the repository**

2. **Install Backend Dependencies**
   ```bash
   cd backend
   npm install
   ```

3. **Install Frontend Dependencies**
   ```bash
   cd frontend
   npm install
   ```

### Configuration

Update the MongoDB connection string in `backend/app.js`:

```javascript
mongoose.connect("mongodb+srv://<username>:<password>@cluster.mongodb.net/", {
  useNewUrlParser: true
});
```

### Running the App

1. **Start the Backend** (runs on port 5000)
   ```bash
   cd backend
   npm start
   ```

2. **Start the Frontend** (runs on port 3000)
   ```bash
   cd frontend
   npm start
   ```

3. Open `http://localhost:3000` in your browser

---

## API Validation

The backend uses `express-validator` for input validation:

- **Places**: Title (required), Description (min 5 chars), Address (required)
- **Users**: Name (required), Email (valid format), Password (min 6 chars)

---

## Dependencies

### Backend
- `express` — Web framework
- `mongoose` — MongoDB ODM
- `mongoose-unique-validator` — Unique field validation
- `express-validator` — Input validation
- `body-parser` — Request body parsing
- `uuid` — Unique ID generation

### Frontend
- `react` — UI library
- `react-dom` — React DOM renderer
- `react-router-dom` — Routing
- `react-scripts` — Create React App scripts
- `react-transition-group` — Animations

---

## License

ISC