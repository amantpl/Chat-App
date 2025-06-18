**QuickChat** - 
*Realtime Chat Application* 💬

---

<div align="center">
  <img src="client/public/screenshot.jpg" alt="QuickBlog Banner" />
  <h3>A responsive web-based blogging platform for writers and readers</h3>
  <br />
</div>

---

## 🖥️ Live Demo

---

[![Live Demo](https://img.shields.io/badge/Live%20Demo-QuickBlog-2ea44f?style=for-the-badge\&logo=vercel\&logoColor=white)](https://quick-blog-sooty.vercel.app/)

## 📋 Table of Contents

1. [✨ Overview](#✨-overview)
2. [🔥 Features](#🔥-features)
3. [🛠️ Tech Stack](#🛠️-tech-stack)
4. [🚀 Quick Start](#🚀-quick-start)
5. [🗂️ Project Structure](#🗂️-project-structure)
6. [💡 Key Components](#💡-key-components)
7. [🤝 Contributing](#🤝-contributing)
8. [📄 License](#📄-license)

---

## ✨ Overview

QuickChat is a real-time chat application featuring secure authentication, instant messaging powered by Socket.IO, and seamless media sharing—all wrapped in a responsive, user-friendly interface.

---

## 🔥 Features

* 🔒 **JWT Authentication**: Secure login & signup flows
* ⚡ **Real-Time Messaging**: Bi-directional chat via Socket.IO
* 📸 **Image Sharing**: Upload & display images via Cloudinary
* 🟢 **Presence Indicators**: See who’s online/offline
* 🔍 **User Search**: Quickly find contacts
* 👁️ **Read Receipts**: Know when messages are seen
* ✏️ **Profile Customization**: Set avatar & bio
* 📱 **Responsive Design**: Optimized for desktop & mobile

---

## 🛠️ Tech Stack

| Layer         | Technologies                                   |
| ------------- | ---------------------------------------------- |
| **Frontend**  | React 18 · Tailwind CSS · React Router         |
| **Backend**   | Node.js 20 · Express 4 · MongoDB 6 · Socket.IO |
| **Utilities** | Axios · Cloudinary                             |

---

## 🚀 Quick Start

**Prerequisites**:

* Node.js v18+
* MongoDB Atlas account
* Cloudinary account

1. **Clone the repo**

   ```bash
   git clone https://github.com/ChetanSaini12/QuickChat.git
   cd QuickChat
   ```
2. **Install dependencies**

   ```bash
   npm install
   ```
3. **Configure**

   * Create a `.env` file at project root:

     ```ini
     MONGO_URI=your_mongodb_uri
     JWT_SECRET=your_jwt_secret
     CLOUDINARY_CLOUD_NAME=your_cloud_name
     CLOUDINARY_API_KEY=your_api_key
     CLOUDINARY_API_SECRET=your_api_secret
     ```
4. **Start the app**

   ```bash
   npm run dev
   ```
5. **Visit** [http://localhost:3000](http://localhost:3000) to start chatting.

---

## 🗂️ Project Structure

```
QuickChat/
├── client/              # React frontend
│   ├── public/          # Static assets (e.g., screenshot.png)
│   └── src/
│       ├── components/  # ChatWindow, LoginForm, etc.
│       ├── context/     # Auth & socket context
│       ├── pages/       # Route views
│       └── utils/       # API services & helpers
├── server/              # Express backend
│   ├── config/          # DB & Cloudinary setup
│   ├── controllers/     # Route handlers
│   ├── models/          # Mongoose schemas
│   ├── routes/          # API endpoints
│   └── middleware/      # Auth & error handling
├── .env                 # Env variables
└── README.md            # Documentation
```

---

## 💡 Key Components

**ChatWindow\.jsx**

```jsx
import { useEffect, useState, useContext } from 'react';
import { SocketContext } from '../context/socket';

const ChatWindow = ({ roomId }) => {
  const socket = useContext(SocketContext);
  const [messages, setMessages] = useState([]);

  useEffect(() => {
    socket.emit('join', roomId);
    socket.on('message', msg => setMessages(prev => [...prev, msg]));
    return () => socket.off('message');
  }, [roomId]);

  return (
    <div className="chat-window">
      {messages.map((m,i) => (
        <p key={i}><strong>{m.user}:</strong> {m.text}</p>
      ))}
    </div>
  );
};
export default ChatWindow;
```

---

## 🤝 Contributing

1. Fork the repo
2. Create a branch: `git checkout -b feature/awesome-chat`
3. Commit: `git commit -m "feat: add new feature"`
4. Push: `git push origin feature/awesome-chat`
5. Open a PR

Please follow code standards and include tests where possible.

---

---

*Made by Aman Thapliyal*
