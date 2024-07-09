# zenn
Collection of articles posted on [Zenn](https://zenn.dev/g_ohara).
## Preview articles
You need to have [Docker](https://www.docker.com/) installed on your computer.
1. Run:
   ```sh
   docker run --rm -p8000:8000 -v$(pwd):/zenn motomotomato/zenn-cli
   ```
   Or if you have [Docker Compose](https://docs.docker.com/compose/), simply run:
   ```sh
   docker compose up -d
   ```
1. Open http://localhost:8000 in your browser.
