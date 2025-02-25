# 24 Web Services with Apache

<iframe src="https://www.youtube.com/embed/PFvFsiLSu94?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Checking Installed Web Services**
    - Web services can run on **different software**, such as Apache, Nginx, or HTTPD.
    - `systemctl status <service>` checks whether a service is **installed and running**.
    - `systemctl status apache2` checks Apache on Ubuntu, while `systemctl status httpd` is used for CentOS.
- **Locating Web Configuration Files**
    - Web server configurations are stored in `/etc/`.
    - Apache settings are found in `/etc/apache2/`, while Nginx uses `/etc/nginx/`.
    - Checking `/etc/` helps determine if the service is **installed and configurable**.
- **Understanding Apache Configuration Files**
    - Apache’s configuration files are in `/etc/apache2/apache2.conf`.
    - The `sites-available/` and `sites-enabled/` directories contain **virtual host settings**.
    - Configuration files include **directives for document root, listening ports, and security settings**.
- **Document Root and Serving Content**
    - The **document root** is where website files are stored (`/var/www/html`).
    - Apache listens on `port 80` for HTTP traffic and serves files from this directory.
    - Creating an `index.html` file in `/var/www/html` allows web content to be displayed.
- **Starting and Enabling Apache**
    - `sudo systemctl start apache2` starts the web server.
    - `sudo systemctl enable apache2` ensures Apache **starts automatically on boot**.
    - `systemctl status apache2` confirms if the service is running or inactive.
- **Testing Website Access**
    - Visiting `http://<server_IP>` in a browser loads the `index.html` file.
    - If no `index.html` exists, Apache may display a **directory listing** or an error.
    - Permissions on `/var/www/html` affect whether Apache can serve files properly.
- **Manipulating Website Files**
    - Creating a folder inside `/var/www/html/` (e.g., `sudo mkdir /var/www/html/test`) allows testing subdirectories.
    - If no `index.html` exists, Apache may show the directory contents.
    - Running `sudo touch /var/www/html/test/index.html` creates a blank page in that directory.
- **Downloading and Viewing Web Content via Terminal**
    - `curl <URL>` retrieves web page content directly in the terminal.
    - `wget <URL>` downloads the web page as a file.
    - `ls -l` shows file ownership and permissions, ensuring **web server access**.
- **Securing Web Content**
    - **Restricting file access** prevents unauthorized users from viewing sensitive files.
    - Moving system files like `/etc/shadow` into the web root could expose **user credentials**.
    - Running `chmod 777` on sensitive files makes them accessible to **everyone**, which is a security risk.
- **Understanding Service Persistence**
    - `systemctl enable apache2` ensures the web server **starts on reboot**.
    - `systemctl disable apache2` prevents it from starting automatically.
    - Checking `systemctl status apache2` helps differentiate between a **disabled** and **stopped** service.


---
Next in Playlist: [25 Router Configuration and Mini Hack Completion](25%20Router%20Configuration%20and%20Mini%20Hack%20Completion.md)