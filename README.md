# Realtime Chat Frontend

Frontend UI for a real-time chat application built with React and Vite. It provides authentication screens, a responsive chat interface, profile management, theme switching, and live conversation updates through Socket.IO.

## Features

- User signup and login flows
- Protected routes for authenticated users
- Real-time private chat UI
- Sidebar with contacts and online indicators
- Profile page with profile picture upload
- Message sending with text and image attachments
- Live online user presence
- Theme persistence using localStorage
- Responsive layout for desktop and mobile

## Tech Stack

- React 19
- Vite
- React Router
- Zustand
- Axios
- Socket.IO Client
- Tailwind CSS
- DaisyUI
- react-hot-toast
- Lucide React icons

## Project Structure

```bash
frontend/
├── src/
│   ├── components/
│   ├── constants/
│   ├── lib/
│   ├── pages/
│   ├── store/
│   ├── App.jsx
│   ├── index.css
│   └── main.jsx
├── public/
├── package.json
└── README.md
```

## Setup

1. Install dependencies

```bash
cd frontend
npm install
```

2. Make sure the backend is running first

The frontend expects the backend API to be available locally at:

```bash
http://localhost:5001
```

3. Start the development server

```bash
npm run dev
```

## Available Scripts

- `npm run dev` - Start the Vite development server
- `npm run build` - Build the app for production
- `npm run preview` - Preview the production build locally
- `npm run lint` - Run ESLint checks

## Pages

- `/` - Main chat dashboard, shown only for authenticated users
- `/login` - Login page
- `/signup` - Sign up page
- `/profile` - Profile page for updating user avatar
- `/settings` - Settings page

## UI Flow

### Authentication

Auth state is managed in Zustand using `useAuthStore`.

- `checkAuth()` verifies the current session on app load
- `login()` signs the user in
- `signup()` creates a new account
- `logout()` clears the session

### Chat Experience

Chat state is managed in Zustand using `useChatStore`.

- `getUsers()` loads sidebar contacts
- `setSelectedUser()` opens a conversation
- `getMessages(userId)` loads a chat thread
- `sendMessage()` sends text or image messages
- `subscribeToMessages()` listens for realtime messages via Socket.IO

### Theme

Theme selection is stored in localStorage via `useThemeStore`, so the selected theme persists across reloads.

## Environment and Backend Connection

The frontend talks to the backend API and socket server at `http://localhost:5001`.

Make sure the backend is configured with CORS to allow the frontend origin:

- Frontend dev server: `http://localhost:5173`

## Main Components

- `Navbar` - Top navigation and auth actions
- `Sidebar` - Contact list and online status
- `ChatContainer` - Active conversation view
- `ChatHeader` - Selected user header and presence
- `MessageInput` - Text and image message composer
- `ProfilePage` - Profile image upload screen
- `AuthImagePattern` - Authentication page illustration panel

## State Management

The app uses Zustand stores instead of Redux:

- `useAuthStore` - Auth user, session state, socket connection, online users
- `useChatStore` - Selected user, messages, contacts, and message actions
- `useThemeStore` - UI theme persistence

## Notes

- File uploads are sent as `multipart/form-data`.
- Profile image uploads use the `profilePic` field name.
- Chat image uploads use the `image` field name.
- The chat UI expects the backend to return user and message objects with `profilePic`, `image`, `createdAt`, and MongoDB `_id` fields.

# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh
