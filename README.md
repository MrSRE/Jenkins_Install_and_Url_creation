### Jenkins_Install_and_Url_creation 


#### Jenkins installers are available for several Linux distributions.

- Debian/Ubuntu
- Prerequisites
    - Minimum hardware requirements:
    - 256 MB of RAM
    - 1 GB of drive space (although 10 GB is a recommended minimum if running Jenkins as a Docker container)
 
   - Enable nginx Ubuntu :
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


