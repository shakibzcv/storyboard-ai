![Project Banner](public/screenshots/project-banner.png)

# <img src="public/logo.svg" height="40" alt="Storyboard Logo" style="vertical-align: middle; margin-right: 10px;" /> Storyboard AI: Create Your Story

> **Create professional, AI-powered presentations and storyboards in minutes.**

**Storyboard AI** is a modern, full-stack presentation builder that empowers creators to visualize their stories. Whether you're a filmmaker, marketer, founder, or educator, our tool helps you generate, edit, and export stunning presentations with ease. Leveraging the power of Google Gemini AI, you can turn simple text prompts into complete visual narratives and structured slide decks.

## 📱 App Preview

Here's a quick look at the application in both dark and light themes:

<div align="center">
  <img src="public/screenshots/dark_demo.png" alt="Dark Theme Preview" width="48%" />
  <img src="public/screenshots/light_demo.png" alt="Light Theme Preview" width="48%" />
</div>

## 🚀 Features

- **✨ AI-Powered Presentations**: Describe your topic, and let our Gemini AI engine generate detailed slides, outlines, and HTML visuals automatically.
- **🎨 Interactive Storyboard Studio**: A visual workspace with slide preview, reordering, presentation mode, and element inspectors.
- **📦 Curated Template Inspirations**: Jumpstart your project with a library of agency-level templates across business, growth, tech, and narrative use cases.
- **🖼️ Storyset Illustrations & Stock Assets**: Rich vector graphics and curated imagery ready to insert into your slides.
- **🔄 Project Management**: Organize your decks with a unified dashboard supporting project creation, search, archiving, and trash recovery.
- **📤 Multi-Format Export**: Lossless export directly to PowerPoint (.pptx), PDF (.pdf), or raw HTML for offline use and sharing.
- **🔐 Secure Authentication**: Multi-provider user authentication (Credentials + Google OAuth) with session management powered by Better Auth.
- **🌓 Dark/Light Mode**: Full responsive design with seamless dark/light theme switching and keyboard shortcuts.

## 🛠️ Tech Stack

- **Framework**: [Next.js 16](https://nextjs.org/) (App Router, Turbopack)
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **UI Library**: [React 19](https://react.dev/), [Tailwind CSS v4](https://tailwindcss.com/) & [Shadcn UI](https://ui.shadcn.com/)
- **Animation**: [Framer Motion](https://www.framer.com/motion/)
- **Database & ORM**: [PostgreSQL (Neon)](https://www.postgresql.org/) with [Prisma](https://www.prisma.io/)
- **AI Engine**: [Google GenAI (Gemini)](https://ai.google.dev/) via `@google/genai`
- **Object Storage**: [AWS S3](https://aws.amazon.com/s3/) / Cloudflare R2
- **Authentication**: [Better Auth](https://www.better-auth.com/)
- **Transactional Emails**: [Resend](https://resend.com/) with [React Email](https://react.email/)
- **Document Exporters**: [pptxgenjs](https://gitbrent.github.io/PptxGenJS/), [jsPDF](https://github.com/parallax/jsPDF), [html-to-image](https://github.com/bubkoo/html-to-image)

## 📐 Architecture Breakdown

```mermaid
graph TD
    A[User Input / Prompt] -->|Prompt| B(Gemini AI Processing)
    B -->|Generates Outline & Slides| C{Content Engine}
    C -->|HTML Templates| D[Visual Layouts]
    C -->|Text & Speaker Notes| E[Script & Outline]
    D --> F[Storyboard Studio]
    E --> F
    F -->|Real-Time Customization| F
    F -->|Export Engine| G[PowerPoint / PDF / HTML]
```

## 📂 Project Structure

```bash
storyboard-ai/
├── .github/              # GitHub Actions workflows and issue/PR templates
├── .vscode/              # Recommended editor configurations
├── prisma/               # Prisma schema and database migrations
├── public/               # Static assets, branding SVGs, templates, and Storyset illustrations
├── scripts/              # Storage bucket setup and teardown automation scripts
├── src/
│   ├── app/              # Next.js 16 App Router (routes, layouts, API endpoints)
│   │   ├── (auth)/       # Authentication pages (sign-in, sign-up, password recovery)
│   │   ├── (main)/       # Workspace pages (home, editor, templates, account, billing)
│   │   ├── api/          # Server API routes (auth, generate, projects, s3, etc.)
│   │   └── project/      # Dynamic project canvas view (/project/[id])
│   ├── components/       # Reusable React components
│   │   ├── ai-elements/  # AI conversation & streaming chat components
│   │   ├── home/         # Dashboard project grids and creation dialogs
│   │   ├── landing/      # Public landing page sections and showcases
│   │   ├── project/      # Interactive storyboard slide editor canvas & toolbars
│   │   └── ui/           # Shadcn UI / Radix primitive components
│   ├── hooks/            # Custom React hooks (chat, mobile detection, syntax highlighting)
│   ├── inspirations/     # Pre-designed presentation template decks and slide metadata
│   ├── lib/              # Core libraries (Better Auth, Prisma client, S3 utilities, parsers)
│   ├── llm/              # Google GenAI (Gemini) SDK client, prompt pipelines, and tools
│   ├── types/            # TypeScript data models and editor contracts
│   └── proxy.ts          # Authentication middleware and route protection
└── package.json
```

## 🏁 Getting Started

Follow these steps to set up the project locally.

### Prerequisites

- **Node.js** (v20 or higher)
- **pnpm** (Recommended package manager)
- **PostgreSQL** database instance (e.g. Neon, Supabase, or local PostgreSQL)

### Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/shakibzcv/storyboard-ai.git
   cd storyboard-ai
   ```

2. **Install dependencies:**

   ```bash
   pnpm install
   ```

3. **Set up Environment Variables:**

   Create a `.env` file in the root directory by copying the example file:

   ```bash
   cp .env.example .env
   ```

   Then update the values in `.env` with your actual credentials:

   ```env
   # Database
   DATABASE_URL="postgresql://user:password@localhost:5432/storyboard_db"

   # Authentication (Better Auth)
   BETTER_AUTH_SECRET="your_better_auth_secret"
   BETTER_AUTH_URL="http://localhost:3000"
   GOOGLE_CLIENT_ID="your_google_client_id"
   GOOGLE_CLIENT_SECRET="your_google_client_secret"

   # App
   NEXT_PUBLIC_BASE_URL="http://localhost:3000"

   # Gemini AI
   GEMINI_API_KEY="your_gemini_api_key"

   # AWS S3 / Cloudflare R2 Storage
   AWS_REGION="auto"
   AWS_ENDPOINT="your_s3_endpoint"
   AWS_ACCESS_KEY_ID="your_access_key"
   AWS_SECRET_ACCESS_KEY="your_secret_key"
   AWS_S3_BUCKET_NAME="your_bucket_name"

   # Notifications / Emails
   RESEND_API_KEY="your_resend_api_key"
   ```

4. **S3 Storage Bucket Setup:**

   Initialize your storage bucket and CORS settings:

   ```bash
   pnpm run bucket:setup
   ```

5. **Database Setup:**

   Run the migrations to set up your database schema:

   ```bash
   pnpm run db:migrate
   ```

6. **Run the Development Server:**

   ```bash
   pnpm run dev
   ```

   Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## 🤝 Contributing

We welcome contributions to make Storyboard AI even better! Please check out our [Contributing Guide](CONTRIBUTING.md) for details on how to get started.

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📬 Contact

- **Author**: Shakib Khan ([@shakibzcv](https://github.com/shakibzcv))
- **Email**: [shakibzcv@gmail.com](mailto:shakibzcv@gmail.com)
- **Project Repository**: [https://github.com/shakibzcv/storyboard-ai](https://github.com/shakibzcv/storyboard-ai)

## 💖 Acknowledgements

- Built with [Next.js](https://nextjs.org/)
- UI components by [Shadcn UI](https://ui.shadcn.com/)
- Icons by [Lucide](https://lucide.dev/) and [Iconify](https://iconify.design/)
