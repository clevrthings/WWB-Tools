# WWB Tools

Deze website combineert:

1. `BIPT -> WWB Inclusion Lists` (automatische `.ils`)
2. `Frequency Exclusion Builder` (image -> `.csv/.txt/.json/.fxl` via OpenAI)

## Routes

- `/` hoofdpagina met downloadbare `.ils` bestanden
- `/exclusion-builder/` uploadtool voor exclusions
- `/debug` admin/debug pagina (Basic Auth)

## Lokaal draaien

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

cp .env.example .env
# vul OPENAI_API_KEY in

uvicorn app.main:app --host 0.0.0.0 --port 8080
```

## Draaien als systemd service (zonder Docker)

Voorbeeld deploymentpad: `/opt/wwbtools`

```bash
sudo mkdir -p /opt/wwbtools
sudo rsync -a --delete ./ /opt/wwbtools/
cd /opt/wwbtools

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

Kopieer service file:

```bash
sudo cp /opt/wwbtools/wwbtools.service /etc/systemd/system/wwbtools.service
```

Pas in `/etc/systemd/system/wwbtools.service` eventueel `User`, `Group` en paden aan, daarna:

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now wwbtools
sudo systemctl status wwbtools
```

## Hosting op `wwb.clevrthings.com`

1. DNS:
- `A` record `wwb.clevrthings.com` -> jouw server IP

2. Reverse proxy:
- `https://wwb.clevrthings.com` -> `http://127.0.0.1:8080`

3. TLS:
- activeer Let's Encrypt certificaat op `wwb.clevrthings.com`

Nginx voorbeeld:

```nginx
server {
    listen 443 ssl;
    server_name wwb.clevrthings.com;

    ssl_certificate /etc/letsencrypt/live/wwb.clevrthings.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/wwb.clevrthings.com/privkey.pem;

    location / {
        proxy_pass http://127.0.0.1:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```
