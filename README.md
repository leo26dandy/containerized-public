# Docker Stack with Traefik, Portainer, MariaDB and phpMyAdmin

This repository contains a Docker Compose configuration for setting up a web development environment with reverse proxy, container management, database, and database administration tools.

## Components

- **Traefik**: Reverse proxy and load balancer with automatic SSL handling
- **Portainer**: Web-based Docker container management
- **MariaDB**: MySQL-compatible database server
- **phpMyAdmin**: Web interface for MySQL/MariaDB database management
- **mkcert**: Local SSL certificate generator

## Prerequisites

- Docker and Docker Compose installed
- A Docker network named `web` already created
- Domain names configured in your hosts file or DNS

## Getting Started

### 1. Create the required Docker network

```bash
docker network create web
```

### 2. Configure your environment

Before starting the stack, customize the following:

- Review and update domain names in the mkcert environment variables
- Set a secure password for MariaDB in the environment variables
- Confirm port mappings meet your requirements
- Create the necessary directory structure for volumes

### 3. Deploy the stack

```bash
docker-compose up -d
```

## Access the Services

After deployment, you can access the following services:

- Traefik Dashboard: https://traefik.home.com
- Portainer: https://portainer.home.com
- phpMyAdmin: https://phpmyadmin.home.com

## Configuration Details

### SSL Certificates

This setup uses mkcert to generate local development SSL certificates for the domains:
- `*.home.com`
- `*.site.com`
- `*.local.com`

### MariaDB

The MariaDB container is configured with:
- Root password as defined in the environment variables
- Persistent storage in a Docker volume

### Traefik

Traefik is configured with:
- HTTP to HTTPS redirection
- Custom configuration via traefik.yml and dynamic.yml files
- SSL termination

## Customization

You can customize this setup by:
- Changing domain names in the mkcert environment
- Modifying Traefik configuration files
- Adding additional database users/databases through environment variables
- Adding your own themes to phpMyAdmin via the volume mount

## Troubleshooting

Common issues:
- Architecture compatibility (use platform-specific images if needed)
- DNS resolution issues (configure Docker DNS settings)
- Network connectivity problems (check firewall rules)

## Security Notes

- This setup is primarily intended for development use
- Change default passwords before using in any accessible environment
- Consider adding additional security measures for production use
