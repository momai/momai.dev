# momai.dev

A personal homepage built with Traefik for reverse proxying and secure integration with OAuth and OIDC providers. This project serves as a gateway to personal services and projects, focusing on simplicity, security, and scalability.

## Features
- Reverse proxy and load balancing using Traefik.
- OAuth/OIDC authentication for secure access.
- Modular and extensible Docker Compose setup.

## Getting Started
Clone the repository, configure your `.env` file with the required parameters, and start the services using Docker Compose.

```bash
git clone https://github.com/momai/momai.dev.git
cd momai.dev
cp .env.sample .env
docker-compose up -d
