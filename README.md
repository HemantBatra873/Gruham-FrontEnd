# Gruham Frontend

Gruham is a full-stack real estate marketplace web application built with the MERN stack. This repository contains the **frontend** code, developed using **React** (with Vite), **Tailwind CSS**, **Redux**, and **Firebase**. The frontend provides a responsive and intuitive user interface for browsing properties, managing user profiles, creating listings, and searching for real estate with advanced filtering.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
  - [Why React and Vite?](#why-react-and-vite)
  - [Why Tailwind CSS?](#why-tailwind-css)
  - [Why Redux?](#why-redux)
  - [Why Firebase?](#why-firebase)
- [Project Structure](#project-structure)
- [Pages and Components](#pages-and-components)
  - [Pages](#pages)
  - [Components](#components)
- [Custom Styling](#custom-styling)
- [Setup Instructions](#setup-instructions)
- [Environment Variables](#environment-variables)
- [Contributing](#contributing)
- [License](#license)

## Project Overview

The Gruham frontend is a modern, user-friendly interface for a real estate platform. It enables users to sign up, log in (via email/password or Google OAuth), browse property listings, create and manage listings, and contact landlords. The application leverages **React** for dynamic rendering, **Tailwind CSS** for responsive styling, **Redux** for state management, and **Firebase** for image storage and authentication. Custom fonts (Italiana and Marcellus) enhance the aesthetic appeal, creating a polished and professional user experience.

## Features

- **User Authentication**: Supports signup, login, and Google OAuth, with secure JWT-based session management.
- **Profile Management**: Users can update their username, email, password, and avatar, as well as delete their account or log out.
- **Listing Creation and Management**: Authenticated users can create, update, and delete property listings with support for multiple image uploads (up to 6 images, 6MB each).
- **Advanced Search**: Users can filter listings by search term, property type (rent/sale), amenities (parking, furnished), offers, and sort by price or creation date.
- **Responsive Design**: Fully responsive layouts optimized for mobile and desktop using Tailwind CSS.
- **Image Uploads**: Seamless integration with Firebase Storage for uploading and managing listing and profile images.
- **Listing Carousel**: A Swiper-powered carousel on the homepage showcases listings with offers.
- **Contact Landlord**: Users can contact property owners via a mailto link with pre-filled listing details.
- **Protected Routes**: Private routes (e.g., profile, create/update listing) are secured using Redux-based authentication checks.
- **Persistent State**: Redux Persist ensures user session data is retained across page refreshes.
- **Custom Typography**: Italiana and Marcellus fonts provide a sophisticated and elegant look.

## Tech Stack

| Technology       | Purpose                                                  |
|------------------|----------------------------------------------------------|
| React            | JavaScript library for building dynamic user interfaces   |
| Vite             | Fast build tool and development server                   |
| Tailwind CSS     | Utility-first CSS framework for responsive styling        |
| Redux            | State management for user authentication and session data |
| Redux Persist    | Persists Redux state across page refreshes               |
| Firebase         | Handles image storage and Google OAuth authentication    |
| React Router     | Client-side routing for navigation                       |
| Swiper           | Carousel component for showcasing listings               |
| Axios/Fetch      | API requests to the backend                              |

### Why React and Vite?

- **React**: Provides a component-based architecture for reusable UI elements, enabling efficient rendering and state management. Its virtual DOM ensures fast updates, ideal for dynamic real estate listings.
- **Vite**: Offers a lightning-fast development server and optimized build process, reducing development time and improving performance compared to Create React App.

### Why Tailwind CSS?

- **Tailwind CSS**: Enables rapid styling with utility classes, reducing the need for custom CSS. Its responsive design utilities ensure consistent layouts across devices, critical for a real estate platform with diverse user devices.
- **Customization**: Tailwind’s configuration allows integration of custom fonts (Italiana and Marcellus) and theme extensions for a unique aesthetic.

### Why Redux?

- **Redux**: Centralizes state management for user authentication and session data, ensuring consistent state across components. The `userSlice` handles login, update, delete, and logout actions with loading and error states.
- **Redux Persist**: Persists the Redux store in local storage, maintaining user sessions across page reloads, enhancing user experience.

### Why Firebase?

- **Firebase Storage**: Provides a scalable solution for storing listing and profile images, with seamless integration for uploading and retrieving image URLs.
- **Firebase Authentication**: Supports Google OAuth, simplifying third-party login implementation.
- **Environment Variables**: Firebase configuration is securely managed via Vite’s environment variables.

## Project Structure

```
src/
├── assets/                  # Custom fonts (Italiana, Marcellus)
├── components/              # Reusable React components
│   ├── Contact.jsx
│   ├── Header.jsx
│   ├── ListingItem.jsx
│   ├── OAuth.jsx
│   └── PrivateRoute.jsx
├── pages/                   # Page components
│   ├── About.jsx
│   ├── CreateListing.jsx
│   ├── Home.jsx
│   ├── Listing.jsx
│   ├── Profile.jsx
│   ├── Search.jsx
│   ├── Signup.jsx
│   ├── Login.jsx
│   └── UpdateListing.jsx
├── redux/                   # Redux store and slices
│   ├── user/
│   │   └── userSlice.js
│   └── store.js
├── App.jsx                  # Main app component with routing
├── firebase.js              # Firebase configuration
├── index.css                # Global styles with Tailwind directives
├── main.tsx                 # Entry point with Redux provider
└── vite.config.js           # Vite configuration
```

## Pages and Components

### Pages

| Page             | Path                           | Description                                                                 |
|------------------|--------------------------------|-----------------------------------------------------------------------------|
| Home             | `/`                            | Displays a carousel of offer listings and sections for rent/sale listings.   |
| About            | `/about`                       | Provides information about the Gruham platform.                             |
| Signup           | `/signup`                      | Allows users to create an account with email/password or Google OAuth.       |
| Login            | `/login`                       | Handles user login with email/password or Google OAuth.                     |
| Profile          | `/profile` (protected)         | Enables users to update their profile, view/delete listings, and log out.    |
| Create Listing   | `/create-listing` (protected)  | Form for creating new property listings with image uploads.                  |
| Update Listing   | `/update-listing/:listingId` (protected) | Form for updating existing listings.                              |
| Listing          | `/listing/:listingId`          | Displays detailed information about a specific listing with contact option.  |
| Search           | `/search`                      | Advanced search interface with filters for type, amenities, and sorting.     |

### Components

| Component        | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| Contact          | Renders a form to contact the landlord via email for a specific listing.     |
| Header           | Navigation bar with links to home, about, profile, and login/signup.         |
| ListingItem      | Reusable component to display a single listing with image, name, and price.  |
| OAuth            | Google OAuth button for signup/login.                                        |
| PrivateRoute     | Protects routes by redirecting unauthenticated users to the login page.      |

## Custom Styling

- **Fonts**: Italiana (serif, elegant) and Marcellus (serif, sophisticated) are used to create a premium aesthetic, stored in the `assets/` folder and integrated via Tailwind CSS.
- **Tailwind CSS**: Applied globally via `index.css` with custom configurations for fonts and responsive breakpoints. Utility classes are used extensively for layout, spacing, and transitions (e.g., hover effects on buttons).
- **Transitions**: Smooth hover effects on buttons and links enhance interactivity (e.g., `hover:bg-white hover:text-black transition-all delay-150 ease-in`).

## Setup Instructions

1. **Clone the repository**:

```bash
git clone https://github.com/HemantBatra873/Gruham-FrontEnd.git
cd gruham-frontend
```

2. **Install dependencies**:

```bash
npm install
```

3. **Set up environment variables**:

Create a `.env` file in the root directory:

```
VITE_FIREBASE_API=your_firebase_api_key
VITE_BACKEND_URL=your_backend_api_url
```

4. **Run the development server**:

```bash
npm run dev
```

The application will be available at `http://localhost:5173` (default Vite port).

5. **Build for production**:

```bash
npm run build
```

## Environment Variables

| Key                 | Description                              |
|---------------------|------------------------------------------|
| VITE_FIREBASE_API   | Firebase API key for authentication and storage |
| VITE_BACKEND_URL    | URL of the Gruham backend API            |

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m "Add your feature"`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

Please ensure code follows the project's ESLint and Prettier configurations.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Maintainer

Gruham Frontend is built and maintained by Hemant Batra. For issues or suggestions, please open an issue on GitHub.
