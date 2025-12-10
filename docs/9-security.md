# 9. Security

This section explains how the documentation website and the cPouta demo environment were secured.

---

## 9.1 Static Site Architecture

The website is built with **MkDocs Material** and is a fully **static site** (HTML, CSS, JS, JSON). It does not include backend logic, databases, logins, or form handling.

Because of this:

- **SQL injection is not possible** (no database)
- **XSS via search is not possible** (search runs client-side and treats input as text)
- **Session, cookie, and request-forgery attacks do not apply** (no authentication or state)

A static site removes many common web vulnerabilities.

---

## 9.2 Access Control and SSH Security

The cPouta VM hosting the website is protected using:

### **SSH key authentication**
- Only SSH keys are allowed  
- Password login is disabled  

### **Security groups (firewall rules)**
Only required ports are open:

- **22** – SSH (restricted using CIDR)  
- **80** – HTTP (used for certificate setup)  
- **443** – HTTPS (public website)

All other inbound traffic is blocked.

---

## 9.3 System Hardening

After VM creation:

1. System was updated:
       sudo apt update && sudo apt upgrade -y

2. Only necessary software was installed:
   - **Nginx** (web server)  
   - **Certbot** (HTTPS)  
   - **Docker** (optional demo)

3. No extra services were exposed.

4. The site is served using a minimal Nginx configuration from `/var/www/html/`.

---

## 9.4 HTTPS and TLS Certificates

The website uses **HTTPS** to protect users by encrypting traffic and preventing interception.

HTTPS is enabled with **Let’s Encrypt** and Certbot:

       sudo certbot --nginx -d yourdomain.com

Certbot:

- installs the TLS certificate  
- configures Nginx  
- redirects HTTP → HTTPS  
- renews certificates automatically  

---

## 9.5 Summary

- Static site → eliminates many vulnerabilities  
- SSH key authentication → protects VM access  
- Security groups → only essential ports open  
- System kept updated and minimal  
- HTTPS → encrypts all traffic  
- No sensitive data is processed or stored  
