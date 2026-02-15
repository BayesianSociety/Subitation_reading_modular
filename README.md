# Subitation_reading_modular

This setup is designed for your goal:
- Transfer the project to another computer.
- Keep editing `data/word-pools_jipjanneke.json`.
- Run the app from Docker Desktop.

The app entry file is:
- `reading.html`

The JSON file used by the app is:
- `data/word-pools_jipjanneke.json`

## Files prepared

These files are now in the project:
- `docker-compose.yml` (runs Nginx and serves this folder)
- `README.md` (full instructions)

## Prerequisites on each computer

1. Install Docker Desktop.
2. Start Docker Desktop and wait until it shows Docker is running.
3. Open a terminal.

## Step-by-step: run on your current computer

1. Go to the project folder:

```bash
cd /home/postnl/AI_software/Subitation_reading_modular
```

2. Start the container:

```bash
docker compose up
```

3. Open the app in a browser:

```text
http://localhost:8080/reading.html
```

4. Keep the terminal running while you use the app.

5. To stop the app, press:

```text
Ctrl + C
```

6. To stop and remove the container cleanly:

```bash
docker compose down
```

## Step-by-step: edit JSON and see changes

1. Open this file in your editor:

```text
/home/postnl/AI_software/Subitation_reading_modular/data/word-pools_jipjanneke.json
```

2. Save your changes.

3. Refresh the browser page:

```text
http://localhost:8080/reading.html
```

No image rebuild is needed because the folder is mounted into the container.

## Step-by-step: transfer to another computer and keep editing

Use one of these two transfer methods.

### Method 1: transfer with Git (recommended)

1. Push this project to your Git remote from the current computer.
2. On the new computer, install Docker Desktop.
3. Clone the repository on the new computer:

```bash
git clone <your-repository-url>
```

4. Enter the project folder:

```bash
cd Subitation_reading_modular
```

5. Start the app:

```bash
docker compose up
```

6. Open:

```text
http://localhost:8080/reading.html
```

7. Edit `data/word-pools_jipjanneke.json` on the new computer, save, and refresh browser.

### Method 2: transfer by copying folder (USB/shared drive)

1. Copy the entire project folder `Subitation_reading_modular` to the new computer.
2. Install and start Docker Desktop on the new computer.
3. Open terminal and enter the copied folder:

```bash
cd /path/to/Subitation_reading_modular
```

4. Start the app:

```bash
docker compose up
```

5. Open:

```text
http://localhost:8080/reading.html
```

6. Edit `data/word-pools_jipjanneke.json`, save, and refresh browser.

## Useful Docker commands

Start in background:

```bash
docker compose up -d
```

Show running containers:

```bash
docker compose ps
```

Show logs:

```bash
docker compose logs -f
```

Stop and remove container:

```bash
docker compose down
```

## Port change (if 8080 is busy)

1. Open `docker-compose.yml`.
2. Change:

```yaml
ports:
  - "8080:80"
```

to:

```yaml
ports:
  - "8090:80"
```

3. Restart:

```bash
docker compose down
docker compose up
```

4. Open:

```text
http://localhost:8090/reading.html
```
