# persona

Ride fares for one route across Ola, Rapido and Namma Yatri.

You send a pickup and a drop. The API asks each app for its price and returns the fares side by side, normalized into one response shape.

| Folder | What it is | Live |
|---|---|---|
| [`backend/`](backend) | FastAPI service that scrapes each ride app and compiles the fares | https://persona-backend-inky.vercel.app |
| [`frontend/`](frontend) | React + Vite screen: pickup, drop and a Google map | https://persona-frontend-six.vercel.app |

## What works today

- **The API returns real fares.** `POST /api/v1/get_fares` calls Ola, Rapido and Namma Yatri with app credentials from the environment. Config-driven compilers and per-app sanitizers turn their different responses into one schema. A refreshed Ola token is kept in memory.
- **The screen is a shell.** It collects pickup and drop and shows a map, but the fare it shows is a placeholder and says so on screen. The UI does not call the API yet.

## Run it

```bash
git clone https://github.com/LifeAyush/persona.git
cd persona
```

API, which needs your own ride-app credentials; see [`backend/.env.example`](backend/.env.example):

```bash
cd backend
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
uvicorn main:app --reload
```

Screen, which needs a Google Maps JavaScript API key in `VITE_GOOGLE_MAPS_API_KEY`:

```bash
cd frontend
cp .env.example .env
npm install
npm run dev
```

## History

This repo joins `persona_backend` and `persona_frontend`, with each one's full history kept under its folder. Arun Singh built the Rapido scraper, the compiled fare response, CORS, the duplicate-row fix, and the map shell with its Google Maps integration.

## License

MIT
