

# 🚀 Project Overview

## ⚙️ Tech Stack

- **Next.js**
- **TypeScript**
- **Clerk**
- **GetStream**
- **ShadCN**
- **Tailwind CSS**

## ⚙️Features

### Authentication & Security
- **Secure Login**: Authenticate via Clerk with social sign-on or email/password.
- **Real-time Security**: Ensure data integrity with secure, real-time interactions.

### Meetings & Controls
- **Start & Manage Meetings**: Initiate and control meetings with ease.
- **Meeting Customization**: Configure settings like recording, reactions, and screen sharing.

### Scheduling & History
- **Schedule Future Meetings**: Plan ahead and manage upcoming meetings effortlessly.
- **Access Past Meetings**: Review details and recordings of previous sessions.

### User Experience
- **Responsive Design**: Seamlessly adapts to various devices for optimal user experience.
- **Personal Meeting Rooms**: Instantly accessible with unique links for quick collaboration.

# 🛠️ Quick Setup

### Requirements

- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/en)
- [npm](https://www.npmjs.com/)

### Getting Started

1. **Clone the Repository**

   ```bash
   git clone https://github.com/adrianhajdin/zoom-clone.git
   cd zoom-clone
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Set Up Environment Variables**

   Create a `.env` file in the root directory and add your credentials:

   ```env
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
   CLERK_SECRET_KEY=
   NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
   NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
   NEXT_PUBLIC_STREAM_API_KEY=
   STREAM_SECRET_KEY=
   ```

4. **Run the Project**

   ```bash
   npm run dev
   ```

5. **Explore Your Project**

   Open [http://localhost:3000](http://localhost:3000) in your browser to view and interact with your application.

---

This format emphasizes clarity, key features, and a step-by-step guide for easy setup, enhancing readability and user engagement.

   ## 🔐 Clerk setup (detailed)

   This project uses Clerk for authentication. Below are the precise steps to create Clerk keys, wire them into this repository, and verify everything works.

   1) Create or select a Clerk application
   - Sign in to https://clerk.com and open the Dashboard.
   - Create a new application (e.g. "LYNK Local") or select an existing one.

   2) Get the publishable (frontend) key
   - In the Clerk Dashboard find the Frontend / Publishable key (often labeled "Publishable key" or shown in the API Keys section).
   - Copy the publishable key and place it into the project's root `.env` as:

      NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_...your_publishable_key...

      Notes: keys prefixed with `NEXT_PUBLIC_` are exposed to the browser and are intended for client SDK usage.

   3) Get the secret (server) key
   - In Clerk Dashboard → API Keys (or Server section) generate/copy the Secret Key.
   - Add it to `.env` as:

      CLERK_SECRET_KEY=sk_...your_secret_key...

      Important: do NOT prefix the secret key with `NEXT_PUBLIC_`. Keep this secret only in server-side environment variables.

   4) Configure allowed origins / redirect URLs in Clerk
   - Add `http://localhost:3000` to Allowed Origins / Redirect URLs for local development. Add your production domain(s) for deployment.

   5) Where to put these values
   - This repo already includes a `.env` with these variables. Edit the file at the project root and paste your keys there.
   - Example `.env` (do NOT commit real secrets):

      NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
      CLERK_SECRET_KEY=
      NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
      NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up

   6) Restart the dev server
   - Stop any running Next.js dev server and run:

      npm run dev

      This makes Next load the new environment variables.

   7) Verify integration
   - Visit `/sign-in` and `/sign-up` or use the app UI to sign in. After success, you should see a user session in the Clerk Dashboard → Users.
   - Check browser network requests to confirm requests to Clerk endpoints succeed (200s). If server-side calls return 401, check that `CLERK_SECRET_KEY` is present in the server environment.

   Security and notes
   - Never commit `CLERK_SECRET_KEY` (or any secret) to git. The repo's `.gitignore` already excludes `.env`.
   - Use your hosting provider's secret manager (Vercel, Netlify, etc.) to store production keys and set the same environment variable names there.
   - If a secret is accidentally exposed, rotate it in the Clerk Dashboard immediately.

   If you'd like, I can add a short `README` snippet showing environment variables for Vercel / GitHub Actions or scan the repo for files that require server-side Clerk access.
