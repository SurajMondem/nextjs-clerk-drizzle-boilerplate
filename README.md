# Next.js + Clerk + Drizzle Boilerplate

A modern, production-ready boilerplate built with **Next.js 15**, **Clerk** authentication, **Drizzle ORM**, and **Neon Database**. This boilerplate provides a solid foundation for building full-stack applications with user authentication, database management, and modern UI components.

## ✨ Features

- 🚀 **Next.js 15** with App Router and Turbopack
- 🔐 **Clerk Authentication** - Complete auth solution with social logins
- 🗄️ **Drizzle ORM** - Type-safe database operations
- 🐘 **Neon Database** - Serverless PostgreSQL
- 🎨 **Tailwind CSS** - Utility-first CSS framework
- 🧩 **Radix UI** - Accessible, unstyled UI components
- 📱 **Responsive Design** - Mobile-first approach
- 🔒 **Protected Routes** - Middleware-based route protection
- 🪝 **Webhooks** - Clerk user sync with database
- 📊 **TypeScript** - Full type safety

## 🚀 Quick Start

### Prerequisites

- Node.js 18+
- npm, yarn, pnpm, or bun
- A Neon database account
- A Clerk account

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd nextjs-clerk-drizzle-boilerplate
```

### 2. Install Dependencies

```bash
npm install
# or
yarn install
# or
pnpm install
# or
bun install
```

### 3. Environment Variables

Create a `.env` file in the root directory:

```env
# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_...
CLERK_SECRET_KEY=sk_test_...
CLERK_WEBHOOK_SECRET=whsec_...

# Database
DATABASE_URL=postgresql://username:password@host/database?sslmode=require
```

#### Getting Your Environment Variables:

**Clerk Configuration:**

1. Visit [Clerk Dashboard](https://dashboard.clerk.com/)
2. Create a new application or select existing one
3. Go to **API Keys** section
4. Copy `Publishable Key` → `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY`
5. Copy `Secret Key` → `CLERK_SECRET_KEY`
6. Go to **Webhooks** section
7. Create a new webhook with endpoint: `https://your-domain.com/api/clerk`
8. Select `user.created` and `user.updated` events
9. Copy the webhook secret → `CLERK_WEBHOOK_SECRET`

**Neon Database:**

1. Visit [Neon Console](https://console.neon.tech/)
2. Create a new project
3. Copy the connection string → `DATABASE_URL`

### 4. Database Setup

Generate and run migrations:

```bash
# Generate migrations
npx drizzle-kit generate

# Apply migrations
npx drizzle-kit migrate
```

### 5. Configure Clerk Webhook

Update your webhook endpoint in Clerk Dashboard:

- **Endpoint URL**: `https://your-domain.com/api/clerk`
- **Events**: `user.created`, `user.updated`

### 6. Run the Development Server

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) to see your application.

## 📁 Project Structure

```
src/
├── app/
│   ├── api/
│   │   └── clerk/          # Clerk webhook handler
│   ├── globals.css         # Global styles
│   ├── layout.tsx          # Root layout with ClerkProvider
│   └── page.tsx            # Home page with auth
├── components/
│   └── ui/                 # Reusable UI components
├── db/
│   ├── drizzle.ts         # Database connection
│   └── schema.ts          # Database schema
├── lib/
└── middleware.ts          # Clerk middleware for route protection
```

## 🔧 Available Scripts

- `npm run dev` - Start development server with Turbopack
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run lint` - Run ESLint

## 🗄️ Database Schema

The boilerplate includes a `users` table with the following fields:

- `id` - Primary key (synced with Clerk user ID)
- `email` - User email
- `firstName` - User's first name
- `lastName` - User's last name
- `imageUrl` - Profile image URL
- `createdAt` - Account creation timestamp
- `updatedAt` - Last update timestamp
- `isEmailVerified` - Email verification status
- `isActive` - Account active status
- `isDeleted` - Soft delete flag

## 🔐 Authentication Flow

1. Users sign up/in through Clerk
2. Clerk webhook triggers on user creation/update
3. User data is automatically synced to your database
4. Protected routes are handled by Clerk middleware

## 🚢 Deployment

This boilerplate is ready to deploy on:

- **Vercel** (Recommended for Next.js)
- **Netlify**
- **Railway**
- **Any Node.js hosting platform**

### Deployment Checklist:

1. Set all environment variables in your hosting platform
2. Update Clerk webhook URL to your production domain
3. Ensure database migrations are applied
4. Configure production domain in Clerk dashboard

## 🛠️ Customization

### Adding New Database Tables

1. Update `src/db/schema.ts`
2. Generate migration: `npx drizzle-kit generate`
3. Apply migration: `npx drizzle-kit migrate`

### Adding UI Components

This boilerplate uses **shadcn/ui** components. Add new components:

```bash
npx shadcn@latest add [component-name]
```

### Extending Authentication

Clerk provides many authentication features:

- Social logins (Google, GitHub, etc.)
- Multi-factor authentication
- Organization management
- Custom fields

Check the [Clerk documentation](https://clerk.com/docs) for more options.

## 📚 Learn More

- [Next.js Documentation](https://nextjs.org/docs)
- [Clerk Documentation](https://clerk.com/docs)
- [Drizzle ORM Documentation](https://orm.drizzle.team/)
- [Neon Documentation](https://neon.tech/docs)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License.
