# EcoRecycle

EcoRecycle is a web app concept that connects residents with recyclers for recyclable-waste pickups. Residents can post waste with pickup details and an expected price, while recyclers can browse requests, accept pickups, and mark them complete.

## Features

- Landing page explaining the recycling problem, the service, and sample material rates.
- Sign-up and login with resident and recycler roles, powered by Supabase Auth.
- Resident dashboard for posting waste, adding a photo and pickup details, and viewing active requests and completed receipts.
- Recycler dashboard for viewing pickup requests on a map, accepting routes, and marking pickups complete.
- Profile editing, optional browser-based location capture, and impact totals for completed requests.
- Responsive interface with a Three.js Earth background and Leaflet map.

## Project files

- `index.html` — page structure and external library imports.
- `style.css` — layout, visual styling, and responsive rules.
- `script.js` — interactive behavior, Supabase integration, and map logic.

## Run locally

The app is a static website. From the project folder, start a local web server:

```powershell
cd D:\CEP2
py -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000) in your browser. If `py` is not available, use the VS Code Live Server extension or another static web server.

## Supabase setup

The app uses Supabase for authentication and stores pickup requests in a table named `waste_requests`. To use the app with your own Supabase project:

1. Create a Supabase project.
2. Configure the project URL and **publishable** client key in `script.js`.
3. Enable the authentication providers you plan to use. Google sign-in also requires Google OAuth credentials and a matching redirect URL in Supabase.
4. Create `waste_requests` with an auto-generated `id` and columns used by the app: `user_name` (text), `type` (text), `weight` (numeric), `rate` (numeric), `address` (text), `coords` (text), `city` (text), `pincode` (text), `image_data` (text), `status` (text), and `collector_name` (text).
5. Configure and test Supabase Row Level Security (RLS) policies for authenticated users before using real data. Do not put a Supabase `service_role` key or other server-side secrets in browser code.

The app loads Three.js, Leaflet, Supabase JS, Font Awesome, and Google Fonts from external CDN services, so an internet connection is needed for those resources.

## Notes

- Browser location access generally requires HTTPS or localhost and user permission.
- The displayed standard recycling prices are examples and may not reflect current local market rates.
- This project is a frontend prototype; review authentication, database access policies, and data ownership before deploying it for public or production use.
