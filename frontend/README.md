# persona screen

UI for ride prices on one route.

The first screen asks for a pickup and a dropoff and shows a map. The fare it shows is a placeholder and is labelled as one; this screen does not call the fare API yet. Arun Singh built that fare shell, including the Google API integration.

**Live:** https://persona-frontend-six.vercel.app

The fare API is in [`../backend`](../backend).

## How to run

Put a Google Maps JavaScript API key in `.env`, then install dependencies and start the Vite dev server:

```sh
cp .env.example .env   # set VITE_GOOGLE_MAPS_API_KEY
npm install
npm run dev
```

`npm run build` writes a production build. `npm run preview` serves that build locally.
