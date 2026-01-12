# /* ===== package.json ===== */
{
  "name": "birthday-site",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  },
  "dependencies": {
    "next": "14.0.0",
    "react": "18.2.0",
    "react-dom": "18.2.0",
    "framer-motion": "^11.0.0",
    "react-confetti": "^6.1.0"
  }
}

/* ===== tailwind.config.js ===== */
module.exports = {
  content: ["./app/**/*.{js,jsx}"],
  theme: { extend: {} },
  plugins: []
};

/* ===== postcss.config.js ===== */
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};

/* ===== app/globals.css ===== */
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  background: linear-gradient(to bottom, #f9a8d4, #c084fc);
}

/* ===== app/layout.jsx ===== */
export const metadata = {
  title: "Happy Birthday Navya ❤️",
};

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}

/* ===== app/page.jsx (ALL CODE IN ONE FILE) ===== */
"use client";
import { motion } from "framer-motion";
import { useState } from "react";
import Confetti from "react-confetti";

/* ===== COMPONENTS ===== */

function Hero() {
  return (
    <motion.div
      initial={{ opacity: 0, y: -60 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 1 }}
      className="h-screen flex flex-col justify-center items-center text-white text-center px-4"
    >
      <h1 className="text-5xl font-bold">🎉 Happy Birthday Navya 🎉</h1>
      <p className="text-2xl mt-6">
        To the most beautiful girl in my life ❤️
      </p>
    </motion.div>
  );
}

function Message() {
  return (
    <motion.div
      initial={{ opacity: 0 }}
      whileInView={{ opacity: 1 }}
      transition={{ duration: 1 }}
      className="py-20 px-6 text-white text-center"
    >
      <p className="text-2xl max-w-2xl mx-auto leading-relaxed">
        Navya, you make my world brighter every single day.  
        I’m so lucky to have you in my life.  
        May all your dreams come true and your smile never fade. 💖✨  
        <br /><br />
        — Yours, Amaresh ❤️
      </p>
    </motion.div>
  );
}

function Gallery() {
  const images = ["/1.jpg", "/2.jpg", "/3.jpg"];
  return (
    <div className="py-16 grid grid-cols-1 sm:grid-cols-3 gap-6 px-6">
      {images.map((img, i) => (
        <motion.img
          key={i}
          src={img}
          className="rounded-xl shadow-lg"
          initial={{ scale: 0.8, opacity: 0 }}
          whileInView={{ scale: 1, opacity: 1 }}
          transition={{ duration: 0.6 }}
        />
      ))}
    </div>
  );
}

function Celebrate() {
  const [boom, setBoom] = useState(false);

  return (
    <div className="py-20 text-center">
      {boom && <Confetti recycle={false} />}
      <button
        onClick={() => setBoom(true)}
        className="bg-white text-pink-600 px-8 py-3 rounded-xl font-bold shadow-lg hover:scale-105 transition"
      >
        🎂 Celebrate Navya 🎂
      </button>
    </div>
  );
}

/* ===== MAIN EXPORT ===== */
export default function Home() {
  return (
    <div className="min-h-screen">
      <Hero />
      <Message />
      <Gallery />
      <Celebrate />
    </div>
  );
}
