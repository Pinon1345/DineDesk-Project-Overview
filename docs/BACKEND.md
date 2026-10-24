<div align="center">

# 🍽️ DineDesk Backend API

**The production-grade backend powering DineDesk, a modern restaurant web portal and management system.**

[![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-Strict-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Express](https://img.shields.io/badge/Express.js-REST%20API-000000?logo=express&logoColor=white)](https://expressjs.com/)
[![Prisma](https://img.shields.io/badge/Prisma-ORM-2D3748?logo=prisma&logoColor=white)](https://www.prisma.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Neon%20Serverless-4169E1?logo=postgresql&logoColor=white)](https://neon.tech/)
[![Stripe](https://img.shields.io/badge/Stripe-Payments-635BFF?logo=stripe&logoColor=white)](https://stripe.com/)
[![Gemini](https://img.shields.io/badge/Google%20Gemini-AI-4285F4?logo=google&logoColor=white)](https://ai.google.dev/)
[![Vercel](https://img.shields.io/badge/Deployed%20on-Vercel-000000?logo=vercel&logoColor=white)](https://vercel.com/)
[![License](https://img.shields.io/badge/License-Proprietary-red)](#-license)

<p align="center">
  🌐 <strong>Frontend Live Link:</strong> <a href="https://dine-desk-one.vercel.app/">https://dine-desk-one.vercel.app</a>
</p>
<p align="center">
  🌐 <strong>Backend Live Link:</strong> <a href="https://dine-desk-backend.vercel.app">https://dine-desk-backend.vercel.app</a>
</p>

_Built by [DevCore Solutions](#-about-devcore-solutions), building the digital core for modern businesses._

</div>

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Core Libraries](#-core-libraries)
- [AI Integration](#-ai-integration-google-gemini)
- [API Route Structure](#-api-route-structure)
- [Environment Configuration](#-environment-configuration)
- [Local Installation & Development](#-local-installation--development)
- [Deployment on Vercel](#-deployment-on-vercel)
- [Troubleshooting](#-troubleshooting)
- [Security](#-security)
- [Meet the Founders](#-meet-the-founders)
- [About DevCore Solutions](#-about-devcore-solutions)
- [License](#-license)

---

## 📖 Overview

**DineDesk** is a full-featured restaurant web portal and management platform. This repository contains its backend API, designed with **scalability, security, and performance** in mind.

The backend powers:

- Core restaurant business operations (restaurants, menus, bookings)
- Secure user authentication and role-based access control
- Relational data management on a serverless PostgreSQL database
- Online payments, listing fees, and automated webhook handling
- Cloud media uploads and optimized image delivery
- AI-powered recommendations and content generation
- Automated transactional emails and notifications

---

## ✨ Key Features

| Area                  | Capabilities                                                                                                 |
| --------------------- | ------------------------------------------------------------------------------------------------------------ |
| 🔐 **Authentication** | Dual-layer security with Firebase Admin SDK and JWT, HTTP-only cookies, and role-based access control (RBAC) |
| 🏪 **Restaurants**    | Listings, profile management, and discovery                                                                  |
| 📋 **Menus**          | Item management, categories, and pricing                                                                     |
| 📅 **Bookings**       | Table reservations and order tracking                                                                        |
| 💳 **Payments**       | Stripe checkout sessions, customer billing, listing fees, and webhook handling                               |
| 🖼️ **Media**          | Secure image and asset uploads to Cloudinary via custom Multer middleware                                    |
| 🤖 **AI**             | Gemini-powered dish recommendations, description generation, and smart customer insights                     |
| 📧 **Notifications**  | Transactional emails, verification, and alerts through Nodemailer                                            |
| 🛡️ **Reliability**    | Global error handling, structured request validation, and strict type checking                               |

---

## 🏗️ System Architecture

```mermaid
flowchart LR
    Client["🖥️ Frontend<br/>(Web Portal)"] -->|REST /api/v1| API["⚙️ Express + TypeScript<br/>(Vercel Serverless)"]
    API --> DB[("🐘 PostgreSQL<br/>Neon + Prisma")]
    API --> Auth["🔐 Firebase Admin + JWT"]
    API --> Stripe["💳 Stripe"]
    API --> Cloud["☁️ Cloudinary"]
    API --> AI["🤖 Google Gemini"]
    API --> Mail["📧 Nodemailer (SMTP)"]
    Stripe -. webhooks .-> API
```

The backend follows a **modular, type-safe architecture**: routes → controllers → services/data layer, with shared middleware for authentication, validation, uploads, and error handling.

---

## 🧰 Tech Stack

| Layer              | Technology                                                     |
| ------------------ | -------------------------------------------------------------- |
| **Runtime**        | Node.js (v18+)                                                 |
| **Framework**      | Express.js with TypeScript                                     |
| **Database**       | PostgreSQL (Neon Serverless)                                   |
| **ORM**            | Prisma ORM (type-safe queries and migrations)                  |
| **Authentication** | Firebase Admin SDK + JSON Web Tokens (HTTP-only cookies), RBAC |
| **Payments**       | Stripe API                                                     |
| **Media**          | Cloudinary + Multer                                            |
| **AI**             | Google Gemini API (`gemini-1.5-flash`)                         |
| **Email**          | Nodemailer (SMTP with Gmail App Passwords)                     |
| **Hosting**        | Vercel (Serverless Functions)                                  |

---

## 📦 Core Libraries

| Package                           | Purpose                                               |
| --------------------------------- | ----------------------------------------------------- |
| `express`                         | Fast, minimalist web framework for RESTful APIs       |
| `prisma` & `@prisma/client`       | Next-gen ORM for type-safe database access            |
| `firebase-admin`                  | Server-side Firebase SDK for identity management      |
| `stripe`                          | Official Stripe library for transactions and webhooks |
| `cloudinary`                      | Cloud storage and dynamic image manipulation          |
| `@google/genai`                   | Official Google Generative AI SDK for Gemini          |
| `nodemailer`                      | Secure email delivery                                 |
| `bcryptjs`                        | Password hashing                                      |
| `jsonwebtoken`                    | Stateless session handling with JWT                   |
| `cors`, `dotenv`, `cookie-parser` | Security and utility middleware                       |

---

## 🤖 AI Integration (Google Gemini)

Dedicated controllers use the Google Gemini API (`gemini-1.5-flash`) to power platform intelligence:

- ✍️ Generating creative, appealing menu item descriptions
- 🥗 Providing smart culinary and dietary recommendations for users
- 📣 Assisting restaurant managers with automated promotional content

All AI calls are authenticated **server-side** with environment-protected API credentials. Keys are never exposed to the client.

---

## 🔌 API Route Structure

The API follows RESTful principles under the `/api/v1` namespace.

| Route                 | Description                                                 |
| --------------------- | ----------------------------------------------------------- |
| `/api/v1/auth`        | User registration, login, token refresh, and session logout |
| `/api/v1/restaurants` | Restaurant listings, profile management, and discovery      |
| `/api/v1/menus`       | Item management, categories, and pricing                    |
| `/api/v1/bookings`    | Table reservations and order tracking                       |
| `/api/v1/payments`    | Stripe checkout sessions and webhook listeners              |
| `/api/v1/ai`          | Gemini-powered recommendation and content generation        |

---

## ⚙️ Environment Configuration

Create a `.env` file in the project root using this template:

```env
# App
NODE_ENV=development
PORT=5000
FRONTEND_URL=http://localhost:3000

# Database (Neon PostgreSQL)
DATABASE_URL=postgresql://user:password@host/dbname?sslmode=require

# Authentication & Security
JWT_SECRET=super_secret_jwt_key
JWT_EXPIRES_IN=7d
COOKIE_SECURE=false

# Stripe
STRIPE_SECRET_KEY=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...
LISTING_FEE_AMOUNT=20

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Google Gemini AI
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=gemini-1.5-flash

# Firebase Admin SDK
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_CLIENT_EMAIL=your_client_email
FIREBASE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"

# SMTP Email (Nodemailer)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASS=your_app_password
MAIL_FROM="DineDesk <no-reply@dinedesk.com>"

# Default Seed Accounts
SUPERADMIN_EMAIL=superadmin@dinedesk.com
SUPERADMIN_PASSWORD=SuperSecurePassword123!
ADMIN_EMAIL=admin@dinedesk.com
ADMIN_PASSWORD=AdminSecurePassword123!
```

> ⚠️ **Never commit your real `.env` file.** Use strong, unique secrets in production and change the default seed account passwords before going live.

---

## 🚀 Local Installation & Development

**Prerequisites:** Node.js v18+, npm, and a PostgreSQL database (a free [Neon](https://neon.tech/) project works well).

**1. Clone the repository**

```bash
git clone https://github.com/Pinon1345/DineDesk-Backend.git
cd DineDesk-Backend
```

**2. Install dependencies**

```bash
npm install
```

**3. Configure environment variables**

Create your `.env` file as shown in [Environment Configuration](#-environment-configuration).

**4. Generate the Prisma client and run migrations**

```bash
npx prisma generate
npx prisma migrate dev
```

**5. Start the development server**

```bash
npm run dev
```

The API will be available at `http://localhost:5000` (or your configured `PORT`).

---

## ☁️ Deployment on Vercel

The backend runs as a serverless function on Vercel.

1. Import the repository into Vercel.
2. Add every variable from the [environment template](#-environment-configuration) under **Settings → Environment Variables**.
3. Make sure Prisma generates its client during the build. Add this to `package.json`:

   ```json
   {
     "scripts": {
       "postinstall": "prisma generate"
     }
   }
   ```

   Keep `prisma` (the CLI) in `dependencies` so it is available during Vercel's install step.

4. Deploy. For production database changes, run migrations with:

   ```bash
   npx prisma migrate deploy
   ```

5. Set up your Stripe webhook endpoint to point to `https://<your-domain>/api/v1/payments/...` and store its signing secret in `STRIPE_WEBHOOK_SECRET`.

---

## 🛠️ Troubleshooting

| Problem                                                                       | Solution                                                                                                                                              |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `500 FUNCTION_INVOCATION_FAILED` with `@prisma/client did not initialize yet` | Prisma client was not generated during the build. Add `"postinstall": "prisma generate"` to your scripts, then redeploy with the build cache cleared. |
| Database connection errors                                                    | Confirm `DATABASE_URL` is set in Vercel and includes `?sslmode=require` for Neon.                                                                     |
| Stripe webhook signature failures                                             | Check that `STRIPE_WEBHOOK_SECRET` matches the endpoint you configured in the Stripe dashboard.                                                       |
| Firebase private key errors                                                   | Keep the `\n` line breaks in `FIREBASE_PRIVATE_KEY` and wrap the value in double quotes.                                                              |
| Emails not sending                                                            | Use a Gmail **App Password** (not your account password) for `SMTP_PASS`.                                                                             |

---

### 🔑 Demo Credentials

| Role           | Email                     | Password                  |
| -------------- | ------------------------- | ------------------------- |
| 🍜 Customer    | `diner@dinedesk.com`      | `DinerPassword123!`       |
| 👨‍🍳 Vendor      | `owner@dinedesk.com`      | `OwnerPassword123!`       |
| 🛡️ Admin       | `admin@dinedesk.com`      | `AdminSecurePassword123!` |
| 👑 Super Admin | `superadmin@dinedesk.com` | `SuperSecurePassword123!` |

> 💳 **Stripe test card:** `4242 4242 4242 4242` · any future expiry · any CVC · any ZIP

---

## 🔒 Security

- HTTP-only cookies for session tokens
- Role-based access control (RBAC) across protected routes
- Passwords hashed with `bcryptjs`
- CORS restricted to the configured `FRONTEND_URL`
- Secrets and API keys kept server-side through environment variables
- Strict TypeScript typing and structured request validation

If you discover a security issue, please report it privately to the DevCore Solutions team rather than opening a public issue.

---

## 👨‍💻 Meet the Founders

DineDesk was built from the ground up by the two founders of **DevCore Solutions**.

<table>
  <tr>
    <td align="center" width="50%">
      <h3>FOURKAN BIN ILIAS</h3>
      <b>Founder · DevCore Solutions</b><br/>
      Full Stack Developer &amp; Junior Software Engineer
    </td>
    <td align="center" width="50%">
      <h3>KAZI MEHEDI HASAN</h3>
      <b>Co-Founder · DevCore Solutions</b><br/>
      Full Stack Developer &amp; Junior Software Engineer
    </td>
  </tr>
</table>

### Engineering Contributions

- **Architecture & Core Backend:** Engineered the Express/TypeScript modular framework, security middleware, global error handling, and structured request validation.
- **Database Engineering & DevOps:** Designed the Neon PostgreSQL relational schema with Prisma and established serverless deployment workflows on Vercel.
- **Integrations:** Implemented third-party pipelines for Stripe payments, Cloudinary media processing, Firebase authentication, Nodemailer alerts, and Google Gemini AI features.

---

## 🏢 About DevCore Solutions

**DevCore Solutions** is a technology startup founded by two passionate software developers, dedicated to crafting scalable, high-performance web applications and digital solutions.

> _Building the digital core for modern businesses._

---

## 📄 License

This project is **proprietary software** developed and maintained by **DevCore Solutions** for the DineDesk platform. All rights reserved. Unauthorized copying, distribution, or modification is prohibited.

---

<div align="center">

**© 2026 DevCore Solutions · Made by Fourkan Bin Ilias (Pinon) & Kazi Mehedi Hasan (Samin)**

</div>
