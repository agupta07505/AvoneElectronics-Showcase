<p align="center">
  <img src="assets/logo.jpeg" alt="Avone Electronics" width="80" />
</p>

<h1 align="center">Avone Electronics</h1>

<p align="center">
  <strong>Full-Stack Production Web Platform &nbsp;·&nbsp; Next.js 15 &nbsp;·&nbsp; MongoDB &nbsp;·&nbsp; Cloudinary &nbsp;·&nbsp; Vercel</strong>
</p>

<p align="center">
  <a href="https://avoneelectronics.com" target="_blank"><img src="https://img.shields.io/badge/🌐_Live_Site-avoneelectronics.com-7a32eb?style=for-the-badge" alt="Live Site" /></a>&nbsp;
  <img src="https://img.shields.io/badge/Status-Production_Ready-00c853?style=for-the-badge" alt="Status" />&nbsp;
  <img src="https://img.shields.io/badge/Version-1.1.0-blue?style=for-the-badge" alt="Version" />&nbsp;
  <img src="https://img.shields.io/badge/Next.js-15.4-000000?style=for-the-badge&logo=next.js" alt="Next.js" />
</p>

<p align="center">
  <sub>Designed, developed & deployed by <a href="https://www.linkedin.com/in/agupta07505/"><strong>Animesh Gupta</strong></a></sub>
</p>

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Live Website](#-live-website)
- [Key Features](#-key-features)
- [Technology Stack](#-technology-stack)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [Security](#-security)
- [SEO & Performance](#-seo--performance)
- [Deployment](#-deployment)
- [Getting Started](#-getting-started)
- [Developer](#-developer)

---

## 🎯 About the Project

**Avone Electronics** is a production-grade, full-stack web platform built for a real electronics manufacturing company based in Noida, India. The platform serves as the company's official digital presence — featuring a dynamic product catalog, event gallery, contact system with email notifications, and a fully-featured admin CMS panel.

This project was built end-to-end — from initial client discovery and UI/UX design through architecture decisions, development, testing, and production deployment on Vercel.

> **This is not a tutorial clone or a portfolio toy.** It is a live, client-facing product serving real users and managed by a non-technical admin team through the custom CMS.

---

## 🌐 Live Website

| | URL |
|---|---|
| **Production** | [avoneelectronics.com](https://avoneelectronics.com) |
| **Platform** | Vercel (Edge Network) |
| **Domain** | Custom domain with HTTPS |

---

## ✨ Key Features

### 🖥️ Customer-Facing

| Feature | Description |
|---------|-------------|
| **Hero Slider** | Auto-rotating carousel with swipe/touch support, pause-on-hover, and admin-configurable slides |
| **Product Catalog** | Category-filtered product grid with dynamic slug-based detail pages, image galleries, specifications, and WhatsApp inquiry CTAs |
| **Event Gallery** | Chronologically sorted gallery events with lightbox viewer, video support, and lazy-loaded media |
| **About Page** | Dynamic brand story sections and values grid — all editable from the admin panel |
| **FAQ Accordion** | Expandable Q&A section managed entirely through the CMS |
| **Contact Form** | Multi-field form with optional PDF attachment, spam protection, real-time validation, and dual email notifications (admin + user confirmation) |
| **Dark / Light Theme** | System-preference-aware theme toggle with persistence and zero-FOUC rendering |
| **Responsive Design** | Mobile-first layouts tested across phone, tablet, and desktop breakpoints |
| **WhatsApp Integration** | Pre-filled WhatsApp message links with product model number for instant customer inquiry |
| **Google Maps Embed** | Interactive map in the footer showing the company's physical location |

### 🔧 Admin CMS Panel

| Feature | Description |
|---------|-------------|
| **Dashboard** | Session-aware landing page with quick-access panels |
| **Product Manager** | Full CRUD — create, edit, delete products with multi-image upload, categories, specs, featured flags, and visibility toggles |
| **Homepage Manager** | Edit hero slides (image + copy), company intro label/heading/text |
| **Gallery Manager** | Create/edit gallery events with title, date, description, multi-image + video uploads |
| **About Page Manager** | Edit hero content, story sections, and values cards |
| **FAQ Manager** | Add, reorder, and delete FAQ entries |
| **Terms Manager** | Rich text terms & conditions editor |
| **Contact Manager** | View submitted inquiries, update footer contact info and social links |
| **Site Settings** | Site name, tagline, support details, and granular maintenance mode (entire site or per-page targeting) |

### ⚙️ Technical Highlights

| Feature | Description |
|---------|-------------|
| **ISR (Incremental Static Regeneration)** | Pages revalidate automatically for near-instant loads with fresh data |
| **Dynamic Metadata** | Per-page OpenGraph, Twitter Cards, and SEO meta generated from database content |
| **Sitemap & Robots** | Auto-generated `sitemap.xml` with dynamic product URLs and `robots.txt` |
| **Maintenance Mode** | Admin-toggled maintenance with per-page targeting (home, about, products, gallery, FAQ, terms, or entire site) |
| **Middleware Auth Guard** | Edge middleware protects all admin routes and API endpoints |
| **On-Demand Revalidation** | Admin changes trigger targeted revalidation so public pages update instantly |
| **Vercel Analytics** | Built-in traffic and performance analytics |

---

## 🛠️ Technology Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Framework** | Next.js 15 (App Router) | Server components, API routes, ISR, middleware |
| **Runtime** | React 18 | UI rendering, client interactivity |
| **Language** | JavaScript (ES2022+) | Full-stack language |
| **Styling** | CSS Modules | Scoped, component-level styling with no runtime cost |
| **Database** | MongoDB (Native Driver) | Document store for all dynamic content |
| **Media Storage** | Cloudinary | Image/video upload, transformation, and CDN delivery |
| **Email** | Nodemailer | Transactional contact emails with HTML templates |
| **Auth** | Custom session-based | Secure password hashing and HTTP-only cookie sessions |
| **Hosting** | Vercel | Edge deployment, serverless functions, automatic HTTPS |
| **Analytics** | Vercel Analytics | Real-time web analytics |
| **UI Libraries** | LightGallery, React Icons | Gallery lightbox and consistent iconography |
| **Loading UX** | nextjs-toploader | Slim progress bar for route transitions |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         VERCEL EDGE                             │
│  ┌──────────────┐      ┌──────────────┐    ┌──────────────────┐ │
│  │  Middleware   │───▶│  App Router  │───▶│ Server Components│ │
│  │ (auth guard,  │     │  (routing,   │    │  (SSR / ISR with │ │
│  │  maintenance  │     │   layouts)   │    │   revalidation)  │ │
│  │  mode check)  │     └──────────────┘    └──────────────────┘ │
│  └──────────────┘                                               │
│         │                                                       │
│         ▼                                                       │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────────┐   │
│  │  API Routes  │──▶│   Services   │───▶│     MongoDB      │   │
│  │  (REST API)  │    │ (data layer) │    │  (Atlas Cloud)   │   │
│  └──────────────┘    └──────────────┘    └──────────────────┘   │
│                      ┌──────────────┐    ┌──────────────────┐   │
│                      │  Cloudinary  │    │   Nodemailer     │   │
│                      │  (media CDN) │    │ (email delivery) │   │
│                      └──────────────┘    └──────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

### Request Flow

```
Client Request
     │
     ▼
┌─ Middleware ────────────────────────────────────────────────┐
│  1. Static asset?            → pass through                 │
│  2. Admin route (no session) → redirect to login            │
│  3. Maintenance mode active? → show maintenance page        │
│  4. Otherwise                → continue to page handler     │
└────────────────────────────────────────────────────────────-┘
     │
     ▼
 Page / API Route
     │
     ▼
 Service Layer → MongoDB / Cloudinary / Nodemailer
     │
     ▼
 Response (HTML via ISR cache or JSON)
```

---

## 📁 Project Structure

```
avone-electronics/
├── app/                        # Next.js App Router
│   ├── layout.js               # Root layout (theme, analytics, top loader)
│   ├── page.js                 # Homepage (hero slider, featured products)
│   ├── about/                  # About page
│   ├── products/               # Product listing + dynamic detail pages
│   ├── gallery/                # Event gallery page
│   ├── faq/                    # FAQ page
│   ├── terms/                  # Terms & Conditions
│   ├── maintenance/            # Maintenance mode page
│   ├── admin/                  # Admin CMS panel (protected)
│   │   ├── login/              # Admin authentication
│   │   ├── products/           # Product CRUD
│   │   ├── homepage/           # Homepage content editor
│   │   ├── gallery/            # Gallery event manager
│   │   ├── about/              # About page editor
│   │   ├── faqs/               # FAQ manager
│   │   ├── terms/              # Terms editor
│   │   ├── contact/            # Contact inquiry viewer & settings
│   │   └── settings/           # Site-wide settings & maintenance
│   ├── api/                    # API route handlers
│   ├── sitemap.js              # Dynamic XML sitemap
│   └── robots.js               # robots.txt generator
│
├── components/                 # Reusable React components
│   ├── NavBar.js               # Navigation bar
│   ├── Footer.js               # Footer with contact form & map
│   ├── HeroSlider.js           # Auto-rotating hero carousel
│   ├── ProductCard.js          # Product grid card
│   ├── ProductGallery.js       # Product detail image gallery
│   ├── GalleryEventSection.js  # Gallery event with lightbox
│   ├── FaqAccordion.js         # Expandable FAQ section
│   ├── WhatsAppButton.js       # WhatsApp CTA button
│   └── Admin*.js               # Admin panel components
│
├── services/                   # Data access layer
├── models/                     # Data schemas & field definitions
├── lib/                        # Core utilities (DB, auth, media, cache)
├── utils/                      # Input validation utilities
├── context/                    # React context (ThemeProvider)
├── styles/                     # CSS Modules
├── middleware.js               # Edge middleware (auth + maintenance)
└── public/                     # Static assets
```

---

## 🔐 Security

| Measure | Description |
|---------|-------------|
| **Password Hashing** | Industry-standard key derivation with random salt |
| **Session Management** | Cryptographically random session tokens with server-side storage |
| **HTTP-Only Cookies** | Secure, tamper-proof session cookies (HttpOnly, SameSite, Secure) |
| **Middleware Auth** | Edge middleware blocks all unauthenticated admin access |
| **Spam Protection** | Honeypot field and server-side validation on all public forms |
| **Input Validation** | Comprehensive server-side validators for all user inputs |
| **File Upload Limits** | Restricted file types and size limits with MIME-type validation |
| **Security Headers** | Disabled `X-Powered-By`, no production source maps |

---

## 🔍 SEO & Performance

### SEO

- ✅ Dynamic `<title>` and `<meta description>` per page
- ✅ OpenGraph and Twitter Card metadata with product images
- ✅ Auto-generated `sitemap.xml` including all product detail URLs
- ✅ `robots.txt` via Next.js metadata API
- ✅ Semantic HTML with proper heading hierarchy
- ✅ Structured `alt` text on all images
- ✅ Canonical URLs via `metadataBase`

### Performance

- ✅ **ISR** — Pages served from edge cache with automatic revalidation
- ✅ **Image Optimization** — AVIF/WebP formats via `next/image`
- ✅ **Code Splitting** — Automatic per-route code splitting
- ✅ **Lazy Loading** — Non-critical images load on viewport entry
- ✅ **CSS Modules** — Zero-runtime scoped CSS with no JS overhead
- ✅ **Zero-FOUC Theme** — Inline script sets theme before first paint
- ✅ **Edge Middleware** — Auth and maintenance checks run at the edge
- ✅ **Top Loader** — Slim progress bar for perceived performance during navigation

---

## 🚀 Deployment

```
┌──────────────────┐        ┌──────────────────┐        ┌──────────────────┐
│   GitHub (main)  │──push──▶    Vercel CI     │──build─▶    Edge Network │
│  Private Repo    │        │  Auto Deploy     │        │  Production CDN  │
└──────────────────┘        └──────────────────┘        └──────────────────┘
```

| Step | Details |
|------|---------|
| **1. Push** | Code pushed to the `main` branch on GitHub |
| **2. Build** | Vercel automatically detects the push, runs `next build` |
| **3. Deploy** | Optimized build is deployed to Vercel's global edge network |
| **4. Live** | Production site updated with zero downtime |

- **Branch Previews** — Every PR/branch gets a unique preview URL
- **Rollbacks** — Instant rollback to any previous deployment
- **Custom Domain** — `avoneelectronics.com` with automatic SSL

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- npm 9+
- MongoDB Atlas account
- Cloudinary account

### Setup

```bash
# Clone the repository
git clone https://github.com/agupta07505/AvoneElectronics.git
cd AvoneElectronics

# Install dependencies
npm install

# Configure environment variables
# Create a .env.local file with your MongoDB, Cloudinary, and email credentials

# Start development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view the site.

### Production Build

```bash
npm run build
npm start
```

---

## 👨‍💻 Developer

<table align="center">
  <tr>
    <td align="center">
      <strong>Animesh Gupta</strong><br/>
      <sub>Full-Stack Developer · B.Tech CSE (Data Science) · IIIT Bhopal (2025–2029)</sub><br/><br/>
      <em>I'm Animesh Gupta, a Computer Science student at IIIT Bhopal, pursuing my B.Tech in CSE (Data Science) (2025–2029). I enjoy building real-world web projects that combine clean UI with practical functionality.</em><br/><br/>
      <a href="https://www.linkedin.com/in/agupta07505/">
        <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
      </a>
      <a href="https://github.com/agupta07505">
        <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
      </a>
      <a href="https://www.instagram.com/agupta07505/">
        <img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram" />
      </a>
    </td>
  </tr>
</table>

---

<p align="center">
  <sub>© Avone Electronics. All rights reserved.</sub><br/>
  <sub>Made with ❤️ by <a href="https://www.linkedin.com/in/agupta07505/"><strong>Animesh Gupta</strong></a></sub>
</p>
