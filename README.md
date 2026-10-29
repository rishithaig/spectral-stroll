# Spectral Stroll

A small Vite and React web app that turns a real walk into a spooky adventure. Theme: **Ghost in the Machine**, with an optional Día de los Muertos feel.

## Summary

A walker types a town or city and how long they want to walk, in minutes. A Vercel serverless function sends that to the Gemma model through the Google AI Studio API and gets back a spooky walking adventure with three to five stops. Each stop has a title, a short spooky story, and one small "touch grass" task (for example: find a tree and put your hand on its bark). The app shows the stops as cards.

## MVP features

1. **Input form**: a town or city field and a walk length (minutes) field, with a "Begin the stroll" button.
2. **Gemma-generated walk**: the serverless function calls Gemma and returns three to five stops, each with `title`, `story` and `task`. The React app renders them as cards.

## Out of scope

- User accounts or saved walks
- Real maps, GPS or turn-by-turn routing
- Verifying that the places in the story actually exist
- Sharing, history or a database
- Offline support

## Run locally

```bash
npm install
npm run dev
```

Then open http://localhost:5173/.

Note: plain `npm run dev` serves only the React frontend. To also run the serverless function locally, use `vercel dev` (install the Vercel CLI first with `npm install -g vercel`).

## API key

Get a free key from Google AI Studio and put it in an environment variable called `GEMINI_API_KEY`:

- **Locally**: create a file named `.env.local` in the project root containing `GEMINI_API_KEY=your_key_here`. Git ignores `*.local` files, so it never reaches GitHub.
- **On Vercel**: add `GEMINI_API_KEY` under Project Settings → Environment Variables.

The key is read only by the serverless function and is never written in the code or exposed to the browser.
