# Ireme Voice Studio

Production-ready AI voice studio built with Next.js 16 and Python, powered by Ireme Soft Hub. The app pairs a modern dashboard with a serverless TTS pipeline so you can authenticate users, bill them, and stream generated audio in real time.

## Highlights

- Secure authentication with Better Auth UI and protected routes
- Credits-based billing with Polar and Neon/Postgres for persistence
- Serverless TTS on Modal using Python, Torch, and Chatterbox
- Project library with recent activity stats and inline audio playback
- Responsive Tailwind UI with reusable components and dashboard layouts

## Stack

- Frontend: Next.js 16, TypeScript, Tailwind CSS, Lucide, Sonner
- Backend: Python 3.11, Modal for compute, Torch/Torchaudio, Chatterbox
- Data: Neon Postgres with Prisma
- Payments/Auth: Polar, Better Auth
- Storage: AWS S3 for generated audio

## Project Structure

```
ireme-voice-studio-app/
├── frontend/                 # Next.js app (App Router)
│   ├── src/app               # Routes and layouts
│   ├── src/components        # Reusable UI
│   ├── src/actions           # Server actions (e.g., TTS)
│   ├── src/lib               # Client helpers (auth, config)
│   └── prisma                # Schema and migrations
├── backend/
│   └── text-to-speech        # Modal-based TTS service (Python)
└── README.md
```

## Quick Start

1. Clone your repo into the new folder name:

   ```bash
   git clone <your-repo-url> ireme-voice-studio-app
   cd ireme-voice-studio-app/frontend
   npm install
   ```

2. Configure environment in `frontend/.env`:

   ```env
   DATABASE_URL="your-neon-connection-string"
   BETTER_AUTH_SECRET="your-better-auth-secret"
   BETTER_AUTH_URL="http://localhost:3000"
   POLAR_ACCESS_TOKEN="your-polar-token"
   POLAR_WEBHOOK_SECRET="your-polar-webhook-secret"
   AWS_ACCESS_KEY_ID="your-aws-key"
   AWS_SECRET_ACCESS_KEY="your-aws-secret"
   AWS_REGION="your-aws-region"
   AWS_S3_BUCKET_NAME="your-s3-bucket"
   MODAL_API_URL="your-modal-endpoint"
   MODAL_API_KEY="your-modal-key"
   MODAL_API_SECRET="your-modal-secret"
   ```

3. Set up the database:

   ```bash
   cd frontend
   npx prisma generate
   npx prisma db push
   ```

4. Set up the TTS service:

   ```bash
   cd ../backend/text-to-speech
   python3 -m venv venv
   source venv/bin/activate  # On macOS/Linux
   pip install -r requirements.txt
   modal deploy tts.py
   ```

5. Run the app:

   ```bash
   cd ../../frontend
   npm run dev
   ```

   Visit `http://localhost:3000` to use the dashboard.

## Usage

- Create: Enter text, pick a language/voice, and generate speech.
- Manage: Browse recent audio projects, play files inline, and view stats.
- Account: Update profile and billing, monitor credit usage.

## Scripts

```bash
npm run dev          # Start frontend dev server
npm run build        # Build for production
npm run start        # Run production build
npm run lint         # ESLint checks
npx prisma studio    # Inspect database
npx prisma migrate   # Apply migrations
modal deploy tts.py  # Deploy TTS service
```

## Credits

- Powered by [Ireme Soft Hub](https://github.com/iremesofthub)
