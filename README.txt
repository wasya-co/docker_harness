

mkdir -p ~/projects ~/.openhands
docker run -it --rm \
  -p 8000:8000 \
  -v ~/.openhands:/home/openhands/.openhands \
  -v ~/projects:/projects \
  ghcr.io/openhands/agent-canvas:latest


services:
  openhands:
    image: ghcr.io/openhands/agent-canvas:latest
    ports:
      - "8000:8000"
    volumes:
      - ~/.openhands:/home/openhands/.openhands
      - ~/projects:/projects
    stdin_open: true
    tty: true

=== build the sandbox ===
From: https://pi.dev/docs/latest/containerization

Uses Dockerfile.pi

  docker build -t pi-sandbox -f Dockerfile.pi .

Then start it:

  docker run --rm -it \
    -e OPENAI_API_KEY \
    -v "$PWD:/workspace" \
    -v pi-agent-home:/root/.pi/agent \
    pi-sandbox


