# Subitation_reading# Subitation_reading_modular
# Subitation_reading_modular

From your project folder, run a local HTTP server and open the HTTP URL instead of file://.

  1. In terminal:

  cd /home/postnl/AI_software/Subitation_reading_modular
  python3 -m http.server 8000

  2. In browser, open:

  - http://localhost:8000/reading.html
  - (or http://127.0.0.1:8000/reading.html)

  3. Keep that terminal running while testing.

  Why this works: now the page and data/word-pools_jipjanneke.json are both served over http, so fetch is allowed.

  If port 8000 is busy, use another port:

  python3 -m http.server 8080

  then open http://localhost:8080/reading.html.
  
  
-------------------------------------------------------------------------------------------------------
• Use Docker to serve the folder over HTTP (same reason as Python server: avoids file:// CORS).

  Run directly with docker run

  1. From project dir:

  cd /home/postnl/AI_software/Subitation_reading_modular
  docker run --rm -p 8000:8000 -v "$PWD":/site -w /site python:3.12-slim python -m http.server 8000

  2. Open:
     http://localhost:8000/reading.html

  If using Docker Desktop

  - Same command works from terminal on your host.
  - You can also start/stop the container in Docker Desktop UI after it appears.

  Alternative with Nginx

  docker run --rm -p 8080:80 -v "$PWD":/usr/share/nginx/html:ro nginx:alpine

  Open:
  http://localhost:8080/reading.html

  Notes:

  - Keep container running while using the app.
  - -v "$PWD":... mounts your current files, so edits are reflected immediately.