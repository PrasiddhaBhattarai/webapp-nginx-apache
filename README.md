# webapp

This project can be deployed using either **Nginx** or **Apache HTTP Server**.

## Clone this repo

```bash
git clone <repo-url>
```

## Project Structure

```bash
README.md
about.html
apache.conf
index.html
nginx.conf
style.css
```

---

# Deploying with Nginx

## 1. Install Nginx

Ubuntu/Debian:

```bash
sudo apt update
sudo apt install nginx
```

---

## 2. Copy Configuration

Copy the provided configuration file:

```bash
sudo cp nginx.conf /etc/nginx/sites-available/webapp
```

---

## 3. Enable Site

```bash
sudo ln -s /etc/nginx/sites-available/webapp /etc/nginx/sites-enabled/
```

---

## 4. Test Configuration

```bash
sudo nginx -t
```

---

## 5. Add to /etc/hosts for local testing

```bash
echo '127.0.0.1  webapp.local' | sudo tee -a /etc/hosts
```

---

## 6. Reload Nginx

```bash
sudo systemctl reload nginx
```

---

## 7. Access Application

Open in browser:

```bash
http://localhost
```

---

# Deploying with Apache

## 1. Install Apache

Ubuntu/Debian:

```bash
sudo apt update
sudo apt install apache2
```

---

## 2. Enable Required Modules

```bash
sudo a2enmod rewrite
```

---

## 3. Copy Virtual Host Configuration

```bash
sudo cp apache.conf /etc/apache2/sites-available/webapp.conf
```

---

## 4. Enable Site

```bash
sudo a2ensite webapp.conf
```

---

## 5. Change Apache Port

Since the configuration uses port `8080`, update Apache ports configuration:

Edit:

```bash
sudo nano /etc/apache2/ports.conf
```

Add:

```apache
Listen 8080
```

---

## 6. Reload Apache

```bash
sudo systemctl reload apache2
```

---

## 7. Access Application

Open in browser:

```bash
http://localhost:8080
```

---

    # Troubleshooting

    ## Nginx Test Failed

    Run:

    ```bash
    sudo nginx -t
    ```

    Check syntax errors in `nginx.conf`.

    ---

    ## Apache Site Not Loading

    Check enabled sites:

    ```bash
    sudo apachectl -S
    ```

    Verify Apache is listening on port `8080`:

    ```bash
    sudo ss -tulpn | grep 8080
    ```

    ---

    # Stopping Services

    ```bash
    sudo systemctl stop nginx
    sudo systemctl stop apache2
    ```
    
