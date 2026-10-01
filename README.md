# ElectAR site

The public landing page for ElectAR, the AR practice app for Senior High TVL Electrical Installation and Maintenance.

A static site: `index.html` plus the scene renders in `img/`. No build step.

- **Local preview:** `python -m http.server 8000`, then open http://localhost:8000
- **Deploy:** Vercel builds nothing and serves the folder as-is; every push to `main` redeploys.
