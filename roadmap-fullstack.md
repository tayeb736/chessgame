# 🗺️ خريطة تعلم Full Stack + Mobile Development

> خارطة طريق شاملة من الصفر إلى الاحتراف

---

## 📘 الرموز

| الرمز | المعنى |
|-------|--------|
| ⭐ | أساسي لا بد منه |
| 🔧 | اختياري حسب التخصص |
| 🎯 | مشروع تطبيقي |
| 📚 | مصدر تعلم مقترح |

---

## 1️⃣ الأساسيات المشتركة (Foundation)

### 1.1 الإنترنت كيف يعمل
- ⭐ كيف يعمل DNS
- ⭐ HTTP/HTTPS (Requests, Responses, Status Codes)
- ⭐ Client-Server Architecture
- ⭐ JSON, XML, RESTful APIs
- 🔧 WebSockets, SSE

### 1.2 Git & GitHub
- ⭐ init, add, commit, push, pull, clone
- ⭐ branching & merging
- ⭐ Pull Requests, Code Review
- 🔧 Git Flow, Rebase, Cherry-pick
- 🔧 GitHub Actions (CI/CD)

### 1.3 محرر النصوص
- ⭐ VS Code (extensions, shortcuts, debugger)
- 🔧 Vim/Neovim basics

### 1.4 سطر الأوامر (Terminal)
- ⭐ ls, cd, mkdir, rm, mv, cp
- ⭐ grep, find, cat, less, head, tail
- ⭐ chmod, chown (permissions)
- 🔧 قذائف: Bash, Zsh, PowerShell

### 1.5 مفاهيم برمجية عامة
- ⭐ المتغيرات، أنواع البيانات
- ⭐ التحكم: if, else, loops
- ⭐ الدوال Functions
- ⭐ Scope و Closure
- ⭐ الـ OOP: Classes, Inheritance, Polymorphism
- ⭐ الـ FP: Pure functions, immutability, map/filter/reduce
- ⭐ Async: Callbacks, Promises, async/await
- 🔧 Design Patterns (Singleton, Factory, Observer)
- 🔧 Data Structures & Algorithms (Arrays, Trees, Graphs, Sorting)

---

## 2️⃣ Frontend (الواجهة الأمامية)

### 2.1 HTML
- ⭐ Semantic HTML (header, nav, main, section, article)
- ⭐ Forms & Inputs (validation, labels)
- ⭐ Accessibility (ARIA, alt, roles, tabindex)
- ⭐ SEO basics (meta tags, Open Graph)
- 🔧 Canvas, SVG

### 2.2 CSS
- ⭐ Selectors, Box Model, Specificity
- ⭐ Flexbox & Grid
- ⭐ Position (static, relative, absolute, fixed, sticky)
- ⭐ Responsive Design (Media Queries, Mobile First)
- ⭐ CSS Variables (Custom Properties)
- 🔧 Animations & Transitions
- 🔧 Preprocessors: Sass/SCSS
- 🔧 Frameworks: Tailwind CSS, Bootstrap

### 2.3 JavaScript (JS - Core)
- ⭐ DOM Manipulation (querySelector, events, createElement)
- ⭐ ES6+: let/const, arrow functions, destructuring, spread, template literals
- ⭐ Modules (import/export)
- ⭐ Event Loop, Microtasks vs Macrotasks
- ⭐ Fetch API & AJAX
- ⭐ localStorage, sessionStorage, cookies
- 🔧 Web Workers
- 🔧 Proxy, Reflect, Symbol, Generators

### 2.4 Package Managers
- ⭐ npm / yarn / pnpm
- ⭐ package.json (scripts, dependencies, devDependencies)

### 2.5 Build Tools & Bundlers
- ⭐ Vite (الأسرع والأحدث)
- 🔧 Webpack
- 🔧 Babel (transpiling)
- 🔧 ESLint + Prettier (code quality)

### 2.6 Frameworks (اختر واحداً)
- **React** ⭐ (الأكثر طلباً)
  - Hooks (useState, useEffect, useContext, useReducer, useRef)
  - React Router
  - State Management: Context API, Zustand, Redux Toolkit
  - Next.js (SSR/SSG)
- **Vue.js** 🔧
  - Composition API
  - Vue Router, Pinia
  - Nuxt.js
- **Angular** 🔧
  - Components, Services, DI
  - RxJS, Guards, Interceptors

### 2.7 TypeScript
- ⭐ Types, Interfaces, Generics
- ⭐ Enums, Unions, Utility Types
- ⭐ tsconfig.json
- 🔧 Decorators
- 🔧 Advanced Types (Mapped, Conditional)

### 2.8 Testing (Frontend)
- ⭐ Vitest / Jest
- ⭐ React Testing Library
- 🔧 Playwright / Cypress (E2E)
- 🔧 Storybook

### 🎯 مشاريع Frontend
1. **صفحة هبوط** (HTML + CSS responsive) — عرض أعمال
2. **Todo App** (JS vanilla) — CRUD, localStorage
3. **متجر بسيط** (React + API) — عربة تسوق، تصفية
4. **لوحة تحكم** (React + Chart.js) — إحصائيات، theme toggle
5. **تطبيق طقس** (React + API خارجي) — Geolocation, unit testing
6. **clone لـ Notion** (Next.js + TipTap) — editing, drag & drop

---

## 3️⃣ Backend (الواجهة الخلفية)

### 3.1 اختر لغة

#### 🟢 JavaScript / TypeScript (Node.js)
- ⭐ Express.js / Koa / Fastify
- ⭐ REST API (routing, middleware, error handling)
- ⭐ Authentication (JWT, OAuth2, session-based)
- ⭐ Validation (Zod, Joi)
- ⭐ Rate Limiting, CORS, Helmet (security headers)
- 🔧 WebSockets (Socket.io)
- 🔧 GraphQL (Apollo Server)
- 🔧 ORM: Prisma, TypeORM, Drizzle
- 🔧 Background Jobs: Bull (Redis), Agenda

#### 🔵 Python
- ⭐ Django / FastAPI / Flask
- ⭐ ORM: Django ORM, SQLAlchemy
- ⭐ Pydantic, Alembic (migrations)
- 🔧 Celery (background tasks)
- 🔧 DRF (Django REST Framework)

#### 🟡 Go
- ⭐ net/http, Chi, Gin, Fiber
- ⭐ Database/sql, GORM
- 🔧 Context, goroutines, channels

#### 🟣 PHP
- ⭐ Laravel (Eloquent, Blade, Artisan)
- 🔧 Symfony

### 3.2 قواعد البيانات

#### SQL (علائقية)
- ⭐ PostgreSQL (الأقوى)
- ⭐ MySQL / MariaDB
- ⭐ مفاهيم: Normalization, Joins, Indexes, Transactions, ACID
- ⭐ Migrations (Flyway, Prisma Migrate, Knex)
- 🔧 Performance: EXPLAIN ANALYZE, Query Optimization
- 🔧 Full-Text Search, JSONB

#### NoSQL
- ⭐ MongoDB (document store)
- ⭐ Redis (cache, session store, queues)
- 🔧 Elasticsearch (search engine)
- 🔧 Neo4j (graph database)

### 3.3 DevOps (أساسيات)
- ⭐ Docker (containerize التطبيق)
- ⭐ Docker Compose (multi-container: app + DB + Redis)
- ⭐ CI/CD (GitHub Actions, GitLab CI)
- ⭐ Linux Server Basics (systemd, nginx, supervisor)
- 🔧 Deployment Platforms: Railway, Render, Fly.io, AWS EC2
- 🔧 Domain + SSL (Let's Encrypt, nginx reverse proxy)
- 🔧 Monitoring: Sentry, Prometheus + Grafana

### 3.4 Security
- ⭐ HTTPS everywhere
- ⭐ SQL Injection prevention (parameterized queries)
- ⭐ XSS, CSRF protection
- ⭐ Password hashing (bcrypt, argon2)
- ⭐ JWT secrets management
- 🔧 OWASP Top 10
- 🔧 Penetration testing basics

### 🎯 مشاريع Backend
1. **REST API للمدونة** (CRUD, users, auth, pagination, search)
2. **نظام مصادقة كامل** (register, login, email verification, reset password, refresh tokens)
3. **Chat app مع WebSockets** (rooms, typing indicator, online status)
4. **URL Shortener** (redirect tracking, rate limiting, analytics)
5. **نظام اشتراكات** (Stripe/PayPal integration, webhooks)
6. **E-commerce API** (products, cart, orders, payments, inventory)

---

## 4️⃣ Full Stack (دمج الواجهتين)

### 4.1 Full Stack Frameworks
- ⭐ **Next.js** (React + SSR + API Routes + Middleware)
- 🔧 Nuxt.js (Vue)
- 🔧 Remix
- 🔧 SvelteKit

### 4.2 مفاهيم متقدمة
- ⭐ Server-Side Rendering (SSR) vs Static Generation (SSG) vs CSR
- ⭐ Database Migrations & Seeding
- ⭐ Authentication flow (JWT + refresh, OAuth)
- ⭐ File upload (multer / formidable + S3 / Cloudinary)
- ⭐ Caching (Redis, CDN, HTTP Cache Headers)
- ⭐ Pagination, Filtering, Sorting APIs (cursor vs offset)
- ⭐ Error handling (global error handler, structured logging)
- 🔧 WebSockets for real-time features
- 🔧 Server-Sent Events (SSE)
- 🔧 Message Queues (RabbitMQ / Kafka / Bull)

### 4.3 Environment & Config
- ⭐ .env files (environment variables)
- ⭐ Multi-environment: development, staging, production
- ⭐ Logging (Winston / Pino for Node, structlog for Python)

### 🎯 مشاريع Full Stack
1. **منصة مدونات كاملة** — Next.js + PostgreSQL + Auth + Markdown editor + comments
2. **SaaS boilerplate** — billing, teams, roles, invitations
3. **تطبيق Trello clone** — drag & drop, real-time sync, WebSockets
4. **منصة تعليمية** — courses, lessons, quizzes, progress tracking
5. **تطبيق دردشة جماعي** — rooms, reactions, file sharing, online presence

---

## 5️⃣ Mobile Development (تطبيقات الهاتف)

### 5.1 اختر مساراً

#### 🟣 React Native (JS/TS)
- ⭐ Expo (الأسهل للبدء) / React Native CLI
- ⭐ Navigation (React Navigation)
- ⭐ State Management (same as React: Zustand, Redux)
- ⭐ AsyncStorage, SecureStore
- ⭐ Push Notifications (Expo Notifications / Firebase)
- 🔧 Native Modules (Swift/Kotlin bridges)
- 🔧 Camera, Maps, Biometrics, Payments
- 🔧 EAS Build & Submit (App Store + Play Store)
- 🔧 Over-the-Air Updates (EAS Update / CodePush)

**مميزات:** مشاركة الكود مع الويب (React)، مجتمع ضخم، نضج عالي

---

#### 🔵 Flutter (Dart)
- ⭐ Widgets (Stateless, Stateful, Inherited)
- ⭐ Navigation (GoRouter)
- ⭐ State Management (Riverpod, Bloc, Provider)
- ⭐ Hive / SharedPreferences (local storage)
- 🔧 Platform Channels (Native code)
- 🔧 Firebase Integration
- 🔧 CI/CD: Codemagic

**مميزات:** أداء 60fps، hot reload سريع، واجهة موحدة (Material + Cupertino)

---

#### 🟢 Kotlin Multiplatform (KMP)
- ⭐ Shared logic (business + data layer) بلغة Kotlin
- ⭐ Native UI لكل منصة (Jetpack Compose + SwiftUI)
- 🔧 Compose Multiplatform (UI مشترك)
- 🔧 Ktor Client, SQLDelight

**مميزات:** مشاركة الـ logic فقط، أداء أصلي 100%

---

#### ⚫ Native
- **Android:** Kotlin + Jetpack Compose
- **iOS:** Swift + SwiftUI
**مميزات:** أداء أفضل، وصول كامل لميزات المنصة
**عيب:** كود منفصل لكل منصة

### 🎯 مشاريع Mobile
1. **Todo App** (offline-first, swipe to delete, dark mode)
2. **تطبيق طقس** (geolocation + open API + animated icons)
3. **Chat App** (Firebase Realtime / WebSocket)
4. **E-commerce App** (products, cart, checkout with Stripe)
5. **تطبيق Fitness Tracker** (step counter, charts, notifications)
6. **Social Media clone** (posts, stories, likes, comments, real-time)

---

## 6️⃣ مسار كل تخصص (Roadmap by Role)

### 🧑‍💻 Frontend Developer
```
HTML → CSS → JS → TypeScript → React/Vue → Next.js/Nuxt → Testing
```
- انت بتشتغل على UI/UX، APIs، state management
- لا تهتم كثير بالـ DevOps أو قواعد البيانات العميقة

### 🧑‍💻 Backend Developer
```
JS/Python/Go → Databases → REST/GraphQL → Auth → Docker → CI/CD
```
- تركيزك: APIs، أداء، أمان، scalability

### 🧑‍💻 Full Stack Developer
```
Frontend (كامل) + Backend (كامل)
```
- تعرف كل الطبقات لكنك قد لا تكون عميقاً في كل واحدة
- الأهم: understanding the whole picture + ability to ship alone

### 🧑‍💻 Mobile Developer
```
React Native / Flutter → State Management → Notifications → Stores
```
- أو Native: Kotlin/Swift → Jetpack Compose/SwiftUI → Platform APIs

### 🧑‍💻 DevOps Engineer
```
Linux → Docker → CI/CD → Cloud (AWS/GCP/Azure) → K8s → Monitoring
```

---

## 7️⃣ جدول تعلم مقترح (12 شهراً)

### 🗓 Month 1-2: الأساسيات
- HTML, CSS (Flexbox, Grid, Responsive)
- JavaScript (DOM, Events, Fetch, ES6+)
- Git + GitHub

### 🗓 Month 3-4: Frontend
- إطار عمل: React (Hooks, Router, State)
- TypeScript
- مشروع: Todo App + طقس App

### 🗓 Month 5-6: Backend
- Node.js + Express + REST API
- PostgreSQL (SQL, Joins, Migrations)
- المصادقة (JWT)
- مشروع: Blog API

### 🗓 Month 7-8: Full Stack
- Next.js (SSR + API Routes)
- Docker + Docker Compose + Deploy
- مشروع: مدونة كاملة + متجر

### 🗓 Month 9-10: Mobile (اختياري)
- React Native / Flutter
- Navigation, State, Notifications
- مشروع: Chat App + E-commerce App

### 🗓 Month 11-12: متقدم
- WebSockets, Background Jobs
- CI/CD, Monitoring
- Security (OWASP)
- مشروع: تطبيق كامل مع Real-time features

---

## 8️⃣ مصادر تعلم (Recommended Resources)

### 📖 مجانية
- **FreeCodeCamp** — كل المسارات
- **The Odin Project** — Full Stack عميق
- **MDN Web Docs** — المرجع الأول للويب
- **Roadmap.sh** — كل roadmap محدث

### 💵 مدفوعة (تستحق)
- **Frontend Masters** — عمق في JS/React/TS
- **Epic React (Kent C. Dodds)** — React متقدم
- **TypeScript Deep Dive** — مجاني، الكتاب الأفضل
- **Full Stack React (Hibox)** — عربي

### 🎥 قنوات YouTube
- ~~**The Net Ninja** — كل شيء~~ (كان أفضل خيار، لكن المحتوى قديم)
- **Web Dev Simplified** — شرح مختصر
- **Fireship** — 100 seconds لكل مفهوم
- **Codevolution** — React/Next.js ممتاز
- **Academind / Maximilian Schwarzmüller** — متعمق
- **Traversy Media** — مشاريع كاملة
- **PedroTech** — TypeScript + React + Node
- **Ben Awad** — Full Stack + Humor
- **Elzero Web School** (عربي) — شامل

---

## 9️⃣ نصائح أخيرة

1. **لا تتعلم كل شيء دفعة واحدة** — اختر مساراً واحداً
2. **ابنِ مشاريع حقيقية** — التعلم بالتطبيق أسرع 10x
3. **اقرأ كود غيرك** — GitHub, Open Source projects
4. **اكتب كوداً نظيفاً منذ البداية** — ESLint, Prettier, naming conventions
5. **تعلم debugging** — DevTools, console, logs, breakpoints
6. **تابع التحديثات** — الـ Web يتغير بسرعة
7. **انشر أعمالك** — GitHub Pages, Vercel, portfolios
8. **ساهم في Open Source** — أفضل طريقة للتعلم المتقدم

---

```
التعلم ليس سباقاً، بل رحلة.
المبرمج الجيد ليس من يعرف كل شيء،
بل من يعرف كيف يجد ما لا يعرفه.
```
