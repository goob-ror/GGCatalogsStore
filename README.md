# 🛒 GG Catalogs Store - Minimal Product Catalog Web App

A lightweight, SEO-friendly product catalog built with Next.js. Designed for fast browsing, admin CRUD management, and user rating via localStorage — **no authentication required** for users.

---

## 🚀 Features

### 🧑‍💼 Admin Features
- Add, edit, and delete products
- Update rating and sold numbers
- Upload product images

### 👀 User Features
- Browse product catalog with categories
- View product details
- Rate products (localStorage-based)

### 🔧 Technical Features
- SEO-ready with static rendering (SSG/ISR)
- Image optimization
- Minimalist UI using Tailwind + Shadcn/ui
- Simple localStorage-based rating system

---

## ⚙️ Tech Stack

| Layer          | Technology                           |
|----------------|---------------------------------------|
| **Frontend**   | [Next.js 14](https://nextjs.org) + TypeScript |
| **Styling**    | [Tailwind CSS](https://tailwindcss.com) + [Shadcn/ui](https://ui.shadcn.com) |
| **Backend API**| Next.js API Routes (no Express)       |
| **Database**   | [Supabase PostgreSQL](https://supabase.com) (hosted DB only) |
| **Image Upload**| Supabase Storage or local `/public/images/` |
| **Ratings**    | `localStorage` (no IP or user accounts) |
| **Deployment** | [Vercel](https://vercel.com)          |

---

## 📁 Project Structure

```
src/
├── app/                    # Next.js App Router
│   ├── admin/             # Admin dashboard routes
│   ├── products/          # Product listings and details
│   ├── api/               # API routes for products & ratings
│   └── layout.tsx         # Root layout
├── components/            # Reusable UI components
├── lib/                   # Supabase client, helpers
├── types/                 # TypeScript interfaces
├── stores/                # (Optional) Zustand stores
└── public/                # Static assets like images
```

---

## 🧪 Database Schema (PostgreSQL via Supabase)

### `products` Table

```sql
id UUID PRIMARY KEY
name VARCHAR(255)
description TEXT
price DECIMAL(10, 2)
image_url VARCHAR(500)
category VARCHAR(100)
stock_quantity INTEGER
rating_average DECIMAL(3, 2) DEFAULT 0
rating_count INTEGER DEFAULT 0
sold_count INTEGER DEFAULT 0
created_at TIMESTAMP DEFAULT now()
updated_at TIMESTAMP DEFAULT now()
```

### 🧠 Local Rating System
- Uses `localStorage` to prevent duplicate votes.
- Ratings affect both `rating_count` and `rating_average`.
- Admins can override or adjust ratings manually.

---

## 🛠️ Development Setup

### Clone the repository
```bash
git clone https://github.com/your-org/gg-catalogs.git
cd gg-catalogs
```

### Install dependencies
```bash
pnpm install
```

### Set up environment variables
Create `.env.local`
```env
NEXT_PUBLIC_SUPABASE_URL=your-supabase-url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
```

### Run development server
```bash
pnpm dev
```

### Open app
Visit http://localhost:3000

---

## 📦 Deployment
We recommend deploying to **Vercel** for optimal performance.

1. Connect your GitHub repo
2. Set environment variables (`.env` values)
3. Done! Vercel will auto-deploy on push

---

## 📌 Roadmap Ideas
- Add search and filter
- Admin auth (JWT-based)
- Tagging system for products
- Pagination or infinite scroll
- Soft delete for products

---

## 🙏 License
MIT License — free to use for personal and commercial projects.

---

## ✨ Credits
Built by TeamDSS using modern, minimal tech for fast delivery and clean UX.