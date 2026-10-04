
= Develop and Use =

  ollama pull qwen3-coder:30b
  # ollama run qwen3-coder:30b

  == use pi.dev sandbox ==

    From: https://pi.dev/docs/latest/containerization

    Uses Dockerfile.pi

      docker build -t pi-sandbox -f Dockerfile.pi .

    Then start it:

      docker run --rm -it \
        -v "$PWD:/workspace" \
        -v pi-agent-home:/root/.pi/agent \
        pi-sandbox

  == run a browser with pi.dev ==

    alias brave='/Applications/Brave\ Browser.app/Contents/MacOS/Brave\ Browser'
    brave --remote-debugging-port=9222 --user-data-dir="$HOME/.brave-debug"

    pi mcp add chrome-devtools -- npx -y chrome-devtools-mcp@latest \
      --no-usage-statistics --browserUrl=http://localhost:9222

  == use cursor ==


    docker build -f Dockerfile.cursor -t cursor-sandbox .

    docker run --rm -it \
      -e CURSOR_API_KEY="$CURSOR_API_KEY" \
      -v "$PWD:/workspace" \
      -w /workspace \
      cursor-sandbox