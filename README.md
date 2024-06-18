# cloud-web-hosting-project

## Project Overview:
### - Goal: 
Hosting a WordPress Web Application on AWS EC2 Service using Apache Server.

### - Description:
This project involves hosting a WordPress website on Amazon Web Services (AWS) using an EC2 instance. The website is served using Apache, a popular, robust open-source web server. This setup provides a flexible and scalable solution for hosting WordPress websites in the cloud, allowing for easy adjustments to handle traffic fluctuations and growth.

### - Technologies Used: 
1.  AWS EC2 (Ubuntu)
2. Elastic IP (AWS) 
3. SSH Client: MobaXterm 
4. Apache server
5. MySQL Server
6. WordPress


### - ## Steps along with Commands and Screenshots

### Step 1 (Creating an EC2 instance on AWS)

1. Logged into the AWS Account
2. Clicked on EC2 Dashboard
3. Created an EC2 instance, with allowing network traffic![[1.png]](https://github.com/AnushcaJoshi/ec2-apache-wordpress-site/blob/main/images/1.png)
4. Associated Elastic IP Address with EC2 Instance (To make sure that whenever or whoever wants to access the web app, it is always available on the same IP)![[2.png]](https://github.com/AnushcaJoshi/ec2-apache-wordpress-site/blob/main/images/2.png)
### Step 2 (SSH into EC2 Instance)

1. I have used MobaXterm for connecting to EC2 instance through SSH
2. In MobaXterm under the SSH tab, entered IP address and user name.
3. Then in Advanced tab, used private key to connect![[3.png]](https://github.com/AnushcaJoshi/ec2-apache-wordpress-site/blob/main/images/3.png)

### Step 3 (Update System and Installing Required Software's)

1. To update the system
    
    ```bash
    sudo apt update && sudo apt upgrade
    ```
    
2. Installation of Apache Server
    
    ```bash
    sudo apt install apache2
    ```
    
    To check weather the Apache Server is running or not, I have tried opening a web browser and in URL typed http://ip_address_of_ec2_instance ![[4.png]](https://github.com/AnushcaJoshi/ec2-apache-wordpress-site/blob/main/images/4.png)
    
3. Installation of WordPress
    
    We need PHP, MySQL Server for WordPress so I have installed all these using following command
    
    ```bash
    sudo apt install libapache2-mod-php
    sudo apt install php-mysql
    sudo apt install mysql-server
    ```
    
4. Configured MySQL server for connecting with WordPress by managing/changing the password
    
    1. Logging into SQL as root
        
        ```bash
        sudo mysql -u root
        ```
        
    2. Configured password using following commands inside SQL
        
        ```sql
        ALTER USER 'root'@localhost IDENTIFIED WITH mysql_native_password BY 'new_password';
        -- new_password: created new password for root
        CREATE USER 'new_user_name'@localhost IDENTIFIED BY 'new_password';
        CREATE DATABASE database_name;
        GRANT ALL PRIVILEGES ON database_name.* TO 'new_user_name'@localhost;
        ```
        
    3. After that copied the link of .tar.gz file from the WordPress website (under releases)
        
    4. Executed the following commands in the terminal
        
        ```bash
        cd /tmp
        sudo wet <https://wordpress.org/wordpress-6.5.4.tar.gz>
        tar -xvf wordpress_file.tar.gz
        sudo mv wordpress/ /var/www/html/
        cd /var/www/html/
        cd wordpress
        
        ```
        
    5. Before moving ahead to install wordpress from the browser, I have opened the link http://ip_address_of_ec2_instance//wordpress. Then followed the instructions to connect to the database. Then got an error.
        
    6. Fixed the error by adding the provided configuration code in /var/www/html/wordpress/wp-config.php
        ```bash
        cd wordpress/
        touch wp-config.php
        nano wp-config.php
        ```
	7. After this you can check your default webpage created by WordPress, you can check http://ip_address_of_ec2_instance//wordpress
    
    ## Conclusion
    
    In conclusion, this project showcases the process of setting up a WordPress website on Amazon Web Services. The steps outlined provide a clear guideline to create a flexible and scalable solution for hosting websites in the cloud. This setup ensures that your website can handle traffic fluctuations and growth efficiently. Following these steps will lead to a robust and reliable hosting environment for your web application.

#### *Note: The EC2 instance that I have created is disabled, so none of the above links will not work*





