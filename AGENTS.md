# Base44 Setup Notes

## Project Overview
This is a minimal static HTML project — a single `index.html` file served by nginx.

## Running the App
```bash
docker compose -f docker-compose.base44.yml up -d
```
- nginx:alpine serves `index.html` on host port 3000
- The repo root is bind-mounted read-only into the container, so edits to `index.html` appear immediately on refresh
- No build step, no dependencies, no secrets required

## Verification
- `curl http://localhost:3000/` returns the contents of `index.html`
- Container healthcheck: `wget --spider http://localhost:80/`

## Notes
- The `/app` directory permissions were set to 755 so nginx worker processes can traverse it
- The preview verification browser cannot inject its bridge into a plain HTML page; verify via curl or the user's own preview pane
