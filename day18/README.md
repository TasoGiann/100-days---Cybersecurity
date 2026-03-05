##🛡️ Day 18: DVWA Setup & First SQL Injection

📝 Executive Summary
Web applications are among the most targeted attack surfaces in modern environments. Today, I deployed DVWA (Damn Vulnerable Web Application) on the Ubuntu Server and performed the first SQL Injection attack from Kali Linux.
This exercise simulated a real-world scenario where an attacker exploits unsanitized user input to extract sensitive data directly from a backend database — one of the most critical and widespread vulnerabilities in web security.

💻 Configuration Steps
1️⃣ LAMP Stack Installation
On the Ubuntu Server, I installed Apache, MySQL, PHP, and required extensions.
Command used:
bashsudo apt install apache2 mysql-server php php-mysqli php-gd libapache2-mod-php -y
Result:

Apache2 2.4.58 installed and running ✅
MySQL 8.0.45 installed and operational ✅
PHP 8.3.6 installed with mysqli and gd extensions ✅


2️⃣ DVWA Deployment
Cloned DVWA into the Apache web root and set the correct permissions.
Commands used:
bashcd /var/www/html
sudo git clone https://github.com/digininja/DVWA.git
sudo chown -R www-data:www-data /var/www/html/DVWA
Then configured the database credentials:
bashcd /var/www/html/DVWA/config
sudo cp config.inc.php.dist config.inc.php
sudo nano config.inc.php
Key settings applied:
php$_DVWA['db_server']   = '127.0.0.1';
$_DVWA['db_user']     = 'dvwa';
$_DVWA['db_password'] = 'p@ssw0rd';
$_DVWA['default_security_level'] = 'low';

3️⃣ Database Setup
Created a dedicated MySQL user and database for DVWA.
Commands used:
bashsudo mysql -u root
sqlCREATE DATABASE dvwa;
CREATE USER 'dvwa'@'localhost' IDENTIFIED WITH mysql_native_password BY 'p@ssw0rd';
GRANT ALL PRIVILEGES ON dvwa.* TO 'dvwa'@'localhost';
FLUSH PRIVILEGES;
EXIT;
Result:

Database DVWA created ✅
Dedicated user with limited privileges created ✅
MySQL 8.0 native password authentication configured ✅


4️⃣ DVWA Initialization
From the Kali Linux browser, navigated to the setup page and initialized the database.
URL:
http://192.168..../DVWA/setup.php
Clicked "Create / Reset Database".
Result:

Database created ✅
Users table populated ✅
Redirected to login page ✅


5️⃣ First SQL Injection Attack
Logged into DVWA (admin / password), set security level to Low, and navigated to the SQL Injection module.
Payload used:
1' OR '1'='1
This payload breaks the intended SQL query logic:
sqlSELECT * FROM users WHERE user_id = '1' OR '1'='1';
Since '1'='1' is always true, the WHERE clause returns every row in the table.
Result — all 5 users dumped from the database:

admin admin ✅
Gordon Brown ✅
Hack Me ✅
Pablo Picasso ✅
Bob Smith ✅


🔐 Security Concepts Learned

SQL Injection mechanics and payload structure
LAMP stack deployment and hardening
DVWA environment configuration
Web application attack surface
Difference between sanitized and unsanitized input handling


🧠 Key Takeaway
SQL Injection remains one of the most dangerous vulnerabilities in web applications. A single unsanitized input field can expose an entire database. The defense is straightforward — use prepared statements and parameterized queries — but the attack is devastatingly simple to execute when they are absent.

🏁 Status
✅ LAMP stack installed and verified
✅ DVWA deployed and initialized
✅ MySQL database configured
✅ First SQL Injection attack successful
✅ All database users extracted via payload
