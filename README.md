### Jenkins_Install_and_Url_creation 

#### Installation of Openjdk
    -  Install Openjdk using the following command
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



