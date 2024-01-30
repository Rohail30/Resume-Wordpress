## Setting Up a Microsoft Azure Linux Server And Resume On Wordpress

- **Create Azure Account:**
   - Visit [Microsoft Azure](https://azure.microsoft.com/) and create an account.

- **Create a Virtual Machine (VM):**
   - In the Azure Portal, navigate to "Virtual Machines" and click "Add."
   - Follow the wizard to configure your VM, including selecting a Linux distribution and setting up authentication.

- **Connect to the VM:**
   - Once the VM is created, connect to it using SSH or the Azure Portal's built-in console and follow steps below:

1. **Update & Upgrade Packages:**
   ```
   sudo apt-get update -y
   sudo apt-get upgrade -y
   ```

2. **Install Apache, MySQL, PHP, & Dependencies:**
   ```
   sudo apt-get install apache2 -y
   sudo apt-get install mysql-server -y
   sudo apt-get install php libapache2-mod-php php-mysql -y
   ```

3. **Configure Firewall & Allow Traffic:**
   ```
   sudo ufw enable
   sudo ufw allow 22
   sudo ufw allow 'Apache Full'
   sudo ufw status
   ```

4. **Start MySQL & Create Database:**
   ```
   sudo service mysql start
   sudo mysql
   CREATE USER 'your_username'@'localhost' IDENTIFIED BY 'your_password';
   CREATE DATABASE IF NOT EXISTS your_database_name;
   GRANT ALL PRIVILEGES ON your_database_name.* TO 'your_username'@'localhost';
   ALTER DATABASE your_database_name CHARACTER SET utf8 COLLATE utf8_general_ci;
   FLUSH PRIVILEGES;
   exit
   ```

5. **Download & Install WordPress:**
   ```
   cd /var/www/html/
   sudo wget https://wordpress.org/latest.tar.gz
   sudo tar -xf latest.tar.gz
   sudo mv wordpress your_directory_name
   ```

6. **Configure WordPress:**
   ```
   cd /var/www/html/your_directory_name
   sudo cp wp-config-sample.php wp-config.php
   ```

7. **Update Apache Site Configurations:**
   ```
   cd /etc/apache2/sites-available/
   sudo nano 000-default.conf
   ```
   Update `DocumentRoot /var/www/html/your_directory_name`

8. **Restart Apache to Apply Changes:**
   ```
   sudo service apache2 restart
   ```

9. **Start Building Your Resume:**
    
   After completing these steps, sign up and log in to your WordPress account using the server's IP address to set up your resume.
