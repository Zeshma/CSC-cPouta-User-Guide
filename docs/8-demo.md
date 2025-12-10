# 8. Optional: Demo for Hosting a Website

Here we create nginx container for hosting a simple website.

---

## 8.1 Create directory
This script creates folder called my-demo-website and enters this folder

    mkdir -p ~/my-demo-website
    cd ~/my-demo-website

---

## 8.2 Create docker-compose.yml and index.html
This script creates two files in folder we are in, in this case inside my-demo-website. Script creates files and then starts container.

    cat > docker-compose.yml << 'EOF'
    services:
      web:
        image: nginx:alpine
        container_name: my-demo-website
        ports:
          - "80:80"
        volumes:
          - ./:/usr/share/nginx/html:ro
        restart: unless-stopped
    EOF

    cat > index.html << 'EOF'
    <!DOCTYPE html>
    <html>
    <head>
      <title>Hello World</title>
    </head>
    <body>
        <h1>HELLO WORLD</h1>
    </body>
    </html>
    EOF

---

## 8.2.1 Start the container

    sudo docker compose up -d

---

## 8.2.2 Check container status

    sudo docker ps

Example picture how it should look like
       <p align="center">
    <img src="../images/picture26.png" alt="Screenshot of container after sudo docker ps command" class="guide-screenshot" />
    </p>

---

## 8.3 Access the website
For accessing website we need to open port 80 in cPouta dashboard.

Go to **Network → Security groups → Create security group**. Name it for example ingress port 80
Add rule. We create Custom TPC rule, you can add description if you want. Add 80 in Port
       <p align="center">
    <img src="../images/picture27.png" alt="A screenshot of a cPouta add rule dashboard" class="guide-screenshot" />
    </p>

Now you should be able to access your website using virtual machine floating IP. There should only be text HELLO WORD on the website.