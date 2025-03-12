# 🏠 Homepage Template  

**A customizable and self-hosted dashboard for organizing your services.**  

![My_homepage.png](#)  

## 🚀 Features  
✅ **Fully customizable** – Modify layout, themes, and widgets  
✅ **YAML-based configuration** – No database required  
✅ **Docker & Kubernetes support** – Easy deployment with `docker-compose`  
✅ **Bookmarks & Services management** – Organize your links efficiently  
✅ **Custom CSS & JS support** – Personalize the appearance  

## 📂 File Structure  
- **`backgrounds/`** – Store custom background images  
- **`icons/`** – Custom icons for services  
- **`logs/`** – Logging directory (if used)  
- **`bookmarks.yaml`** – Manage your personal bookmarks  
- **`services.yaml`** – Define and organize self-hosted services  
- **`settings.yaml`** – General settings and configuration  
- **`widgets.yaml`** – Configure dashboard widgets  
- **`custom.css` & `custom.js`** – Customize styles and scripts  
- **`docker.yaml` & `kubernetes.yaml`** – Deployment configurations  

## 🛠️ Installation  

### 🔹 Docker Deployment  

1. **Add the service to your `docker-compose.yml`**  
   Add the following configuration to your existing `docker-compose.yml` file:  

   ```yaml
   homepage:
     image: ghcr.io/gethomepage/homepage:latest
     container_name: homepage
     ports:
       - 3000:3000
     networks:
       - caddy
     env_file: .env
     volumes:
       - './homepage:/app/config' # Make sure your local config directory exists
       # - /var/run/docker.sock:/var/run/docker.sock # (optional) For Docker integrations)
     environment:
       PUID: $PUID # Read from .env
       PGID: $PGID # Read from .env
     restart: unless-stopped
   ```

   *(Optional: Also include Portainer in your `docker-compose.yml` for easy container management.)*  

2. **Deploy the service**  
   Run the following command in the same directory as your `docker-compose.yml`:  
   ```bash
   docker-compose up -d
   ```

3. **Reverse Proxy with Caddy**  
   This setup uses **Caddy** as a reverse proxy to manage access and SSL certificates automatically. Make sure your Caddy configuration includes the necessary proxy settings for `homepage`.  

4. **Access your Dashboard**  
   Open `http://your-domain.com` (or `http://localhost:3000` if not proxied) in your browser to see your **Homepage Dashboard**! 🚀

## 🎨 Customization  
- Edit `services.yaml` to add your apps  
- Modify `settings.yaml` for layout preferences  
- Use `custom.css` & `custom.js` for styling tweaks  

## 📜 License  
This project is open-source under the **MIT License**. Contributions are welcome! 🚀  

---

Ajoute un **screenshot** du dashboard et mets à jour le lien GitHub pour un README encore plus complet ! 😊
