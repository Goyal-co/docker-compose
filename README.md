Certainly! Here’s a **README.md** for your [docker-compose](https://github.com/Goyal-co/docker-compose) repo, designed to be clear for both you and collaborators:

---

# CRM Docker Compose Deployment

This repository contains the **Docker Compose setup** and **Caddy reverse proxy configuration** for deploying the CRM application, which consists of a frontend and backend service.

---

## **Project Structure**

```
/
├── CRM_frontend/      # Frontend code (React/Vue/Angular etc.)
├── CRM_server/        # Backend code (Node.js/Express etc.)
├── Caddyfile          # Caddy reverse proxy configuration
└── compose.yml        # Docker Compose file
```

---

## **How It Works**

- **CRM_frontend** and **CRM_server** are built from their respective Dockerfiles.
- **Caddy** acts as a reverse proxy, handling HTTPS and routing traffic to the frontend and backend.
- All services are orchestrated using `docker compose`.

---

## **Domains & Routing**

- **Frontend:** [https://crm.goyalhariyanacrm.in](https://crm.goyalhariyanacrm.in)
- **Backend/API:** [https://api.goyalhariyanacrm.in](https://api.goyalhariyanacrm.in)

Caddy automatically redirects HTTP to HTTPS and proxies requests to the correct service.

---

## **Getting Started**

### **Prerequisites**

- Docker & Docker Compose installed on your server.
- The `CRM_frontend` and `CRM_server` directories should be present in the same directory as this repo.

### **Clone the Repos**

```bash
git clone https://github.com/Goyal-co/docker-compose.git
cd docker-compose
git clone https://github.com/Goyal-co/CRM_frontend.git
git clone https://github.com/Goyal-co/CRM_server.git
```

### **Start the Services**

```bash
docker compose up --build -d
```

- This will build and start all services in the background.

### **Stop the Services**

```bash
docker compose down
```

---

## **CI/CD Deployment**

This repo is set up for **GitHub Actions** based CI/CD.  
You can manually trigger a deployment workflow that will:

1. SSH into your server.
2. Pull the latest code for frontend and backend.
3. Rebuild and restart the Docker Compose stack.

**Secrets required:**  
- `SSH_PRIVATE_KEY`
- `SSH_USER`
- `SSH_HOST`
- `WORK_DIR`

See `.github/workflows/deploy.yml` for details.

---

## **Configuration Files**

- **Caddyfile:** Handles HTTPS and reverse proxy rules.
- **compose.yml:** Defines all services, networks, and volumes.

---

## **Useful Commands**

- **Rebuild and restart everything:**
  ```bash
  docker compose down
  docker compose up --build -d
  docker image prune -f
  ```

- **View logs:**
  ```bash
  docker compose logs -f
  ```

---

## **Contributing**

Feel free to open issues or submit pull requests for improvements or bug fixes.

---

## **License**

MIT License

---

**Happy deploying! 🚀**