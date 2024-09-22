### Jenkins_Install_and_Url_creation 

#### Installation of Openjdk
   - Install Openjdk using the following command :
     ```bash
        sudo apt update
        sudo apt install fontconfig openjdk-17-jre
        java -version # check java version
        openjdk version "17.0.8" 2023-07-18
        OpenJDK Runtime Environment (build 17.0.8+7-Debian-1deb12u1)
        OpenJDK 64-Bit Server VM (build 17.0.8+7-Debian-1deb12u1, mixed mode, sharing)
     ```

#### Jenkins installers are available for several Linux distributions.

- Debian/Ubuntu
- Prerequisites
    - Minimum hardware requirements:
    - 256 MB of RAM
    - 1 GB of drive space (although 10 GB is a recommended minimum if running Jenkins as a Docker container)
 
   - Install Jenkins :
     ```bash
        sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
        https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
        
        sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
        https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
            
        echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
        https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
        /etc/apt/sources.list.d/jenkins.list > /dev/null

        sudo apt-get update
        sudo apt-get install jenkins
     ```

####  Start Jenkins
 
**You can enable the Jenkins service to start at boot with the command:**
   - enable Jenkins :
     ```bash
      sudo systemctl enable jenkins
     ```

**You can start the Jenkins service with the command:**
   - start Jenkins :
     ```bash
      sudo systemctl start jenkins
     ```

**You can check the status of the Jenkins service using the command:**
   - status check Jenkins :
     ```bash
      sudo systemctl status jenkins
     ```

### Nginx installation and configuration 
**Step 1: steps to install nginx and start**
**install Nginx**
    - Go to Ubuntu system on AWS , Install Nginx 

1. **Install nginx**
   - Install nginx Ubuntu :
     ```bash
     sudo apt-get install nginx -y
     ```
2. **Enable nginx**
   - Enable nginx Ubuntu :
     ```bash
     sudo systemctl enable nginx
     ```
3. **check status of nginx**
   - checking status of nginx :
     ```bash
     sudo systemctl status nginx
     ```
4. **start nginx**
   - start nginx Ubuntu :
     ```bash
     sudo systemctl start nginx
     ```

### Create a New Configuration File for Jenkins

1. **Creating  a new configuration file for Jenkins**
   - Navigate to the Nginx Configuration Directory: :
     ```bash
        cd /etc/nginx/sites-available/
        ##Create a New Configuration File for Jenkins: Instead of modifying the default configuration, create a separate file (e.g., jenkins.conf):
        sudo vi /etc/nginx/sites-available/jenkins.conf
        ## Add the Jenkins Reverse Proxy Configuration: In the jenkins.conf file, add the reverse proxy configuration for Jenkins. Make sure to replace jenkins.yourdomain.com with your cloud DNS URL:
        
        server {
            listen 80;
            server_name jenkins.yourdomain.com;

            location / {
                proxy_pass http://localhost:8080;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;
            }

            client_max_body_size 1G;
            proxy_buffering off;
        }

        ## Save and Exit the File: Save the changes and exit the file.**

     ```

2. **Enable the New Configuration**
   - Create a Symlink to sites-enabled: To enable this configuration, create a symlink from the      sites-available directory to the sites-enabled directory: :
     ```bash
        sudo ln -s /etc/nginx/sites-available/jenkins.conf /etc/nginx/sites-enabled/
        # Ensure Both Configurations Are Active: You should now have two configuration files, one for your default site and one for Jenkins:
        /etc/nginx/sites-available/default (or the existing configuration)
        /etc/nginx/sites-available/jenkins.conf
        # Make sure the symlinks in sites-enabled point to both files:
        ls -l /etc/nginx/sites-enabled/
        # You should see:
        # default -> /etc/nginx/sites-available/default
        # jenkins.conf -> /etc/nginx/sites-available/jenkins.conf
     ```


3. **Check and Restart Nginx**
   - Test Nginx Configuration: Before restarting, verify that your Nginx configuration is valid: :
     ```bash
        sudo nginx -t
        # Restart Nginx: After ensuring the configuration is correct, restart Nginx:
        sudo systemctl restart nginx
     ```


### Jenkins login Page

<img width="933" alt="image" src="https://github.com/user-attachments/assets/5d2860e5-795a-4504-8d17-1d517b0336e7">

<img width="959" alt="image" src="https://github.com/user-attachments/assets/0fe9c871-c6db-49b0-9e86-c62ca8eddee0">
