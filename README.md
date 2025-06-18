**QuickChat**
*Realtime Chat Application* 💬

---

## 📋 Table of Contents

1. [✨ Overview](#-overview)
2. [🔥 Features](#-features)
3. [🛠️ Tech Stack](#️-tech-stack)
4. [🚀 Quick Start](#-quick-start)
5. [🗂️ Project Structure](#️-project-structure)
6. [💡 Key Components](#-key-components)
7. [🤝 Contributing](#-contributing)
8. [📄 License](#-license)

---

## ✨ Overview

QuickChat is a modern real-time chat application built on the MERN stack with Socket.IO for instant messaging. It offers secure authentication, media sharing, and seamless conversations—on desktop and mobile.

---

## 🔥 Features

* 🔒 **JWT Authentication**: Secure login & signup
* ⚡ **Real-Time Messaging**: Powered by Socket.IO
* 📸 **Image Sharing**: Upload & display via Cloudinary
* 🟢 **Status Indicators**: Online/offline presence
* 🔍 **User Search**: Find friends instantly
* 👁️ **Read Receipts**: Know when messages are seen
* ✏️ **Profile Customization**: Set bio & avatar
* 📱 **Responsive Design**: Chat on any device

---

## 🛠️ Tech Stack

| Layer         | Technologies |
| ------------- | ------------ |
| **Frontend**  |              |
|               |              |
|               |              |
| **Backend**   |              |
|               |              |
|               |              |
|               |              |
| **Utilities** |              |
|               |              |

---

## 🚀 Quick Start

**Prerequisites**

* Node.js (v18+)
* MongoDB Atlas account
* Cloudinary account

1. **Clone & install dependencies**

   ```bash
   git clone https://github.com/ChetanSaini12/QuickChat.git
   cd QuickChat
   npm install
   ```

2. **Configure environment variables**

   * Create a `.env` at project root with:

     ```ini
     MONGO_URI=your_mongodb_uri
     JWT_SECRET=your_jwt_secret
     CLOUDINARY_CLOUD_NAME=your_cloud_name
     CLOUDINARY_API_KEY=your_api_key
     CLOUDINARY_API_SECRET=your_api_secret
     ```

3. **Run the application**

   ```bash
   npm run dev
   ```

4. **Open** [http://localhost:3000](http://localhost:3000) and start chatting!

---

## 🗂️ Project Structure

```
QuickChat/
├── client/              # React frontend
│   ├── public/          # Static assets (avatars, etc.)
│   └── src/
│       ├── components/  # UI components (ChatWindow, LoginForm)
│       ├── context/     # Auth & socket context
│       ├── pages/       # Route views
│       └── utils/       # API services & helpers
├── server/              # Express backend
│   ├── config/          # DB & Cloudinary setup
│   ├── controllers/     # Route handlers
│   ├── models/          # Mongoose schemas
│   ├── routes/          # API endpoints
│   └── middleware/      # Auth & error handling
├── .env                 # Environment variables
└── README.md            # Documentation
```

---

## 💡 Key Components

### ChatWindow Component

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
      {messages.map((m,i) => <p key={i}><strong>{m.user}:</strong> {m.text}</p>)}
    </div>
  );
};
export default ChatWindow;
```

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/awesome-chat`
3. Commit your changes: `git commit -m "feat: add new feature"`
4. Push: `git push origin feature/awesome-chat`
5. Open a Pull Request

Please adhere to the code style and write tests where appropriate.

---

##
