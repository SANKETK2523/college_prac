Assignemnt 6 Exploring Containerization and Application Deployment with Docker
🐳 My First Docker Project (Apache Web Server on AWS EC2)

Hi future me 👋, This is what I did today step by step. Read it like a story so you don’t forget 🚀

🌍 What I wanted to do
Make a tiny website that says “Hello, Docker!”
Put it inside a Docker container with Apache web server
Run it on my AWS EC2 instance (cloud computer)
Open it in a browser at http://<my-ec2-ip>:8080
🧰 Tools I used
AWS EC2 (Ubuntu machine = my cloud laptop 💻☁️)
Docker (to make containers 🐳)
Apache (httpd) (to serve my web page 🍽️)
☁️ Steps for AWS EC2 Setup
Create EC2 Instance

Chose Ubuntu 22.04 (free tier t2.micro).

Created key pair (.pem file) to connect.

In Security Group, opened ports:

22 (SSH) → so I can connect
8080 (TCP) → so I can see my website
Connect to EC2 (from my computer terminal):

ssh -i mykey.pem ubuntu@<EC2-Public-IP>
Update EC2 and Install Docker:

sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu
👣 Steps I took for Docker Project (like a recipe)
Make a folder for my project

mkdir mydockerapp
cd mydockerapp
Create a simple web page

echo "<h1>Hello, Docker!</h1>" > index.html
Create a Dockerfile

vim Dockerfile
FROM httpd:2.4
COPY index.html /usr/local/apache2/htdocs/
:wq! ((save the file)
👉 This means:

“Hey Docker, use Apache as base”
“Copy my index.html inside Apache’s web folder”
Build my Docker image

sudo docker build -t my-apache-server .
Run my container

sudo docker run -p 8080:80 -d my-apache-server
👉 This means:

Port 80 inside container → Port 8080 on EC2
Run in background mode
Check it’s running

docker ps
Open in browser

http://<EC2-Public-IP>:8080
🎉 I saw my page: Hello, Docker!

🧹 Cleanup (if needed)
Stop the container:

docker stop <container_id>
Remove container:

docker rm <container_id>
Remove image:

docker rmi my-apache-server
🎯 What I learned
EC2 = my computer in the cloud ☁️
Docker = magic box for apps 🪄
Apache = waiter who serves my web page 🍽️
Port mapping = “Hey outside world, talk to my container through this door 🚪”
📘 Quick Docker Commands (cheat sheet for future me)
See running containers:

docker ps
See all containers (even stopped ones):

docker ps -a
List all images:

docker images
Stop container:

docker stop <id>
Remove container:

docker rm <id>
Remove image:

docker rmi <image-name>
Assignemnt 8 - Practical Maven Assignment
Step-by-Step Explanation of maven_setup.sh
1️⃣ Update the system
sudo apt update -y
Think of this as telling your Ubuntu computer to check for the latest toy updates.
apt update makes sure your computer knows about the newest software packages.
2️⃣ Install Java
sudo apt install -y openjdk-17-jdk
Java is like a magic engine that can run programs written in Java.
We installed OpenJDK 17, a free version of Java.
-y means “Yes, I want to install it” without asking every time.
3️⃣ Install Maven
sudo apt install -y maven
Maven is like a recipe manager for Java projects.
It knows how to build projects, download libraries, and run web apps.
4️⃣ Check if Java & Maven work
java -version
mvn -version
This is like testing if our magic engine and recipe manager are ready.
It prints the version so you know everything installed correctly.
5️⃣ Set some variables
APP_NAME="my-webapp"
GROUP_ID="com.example"
APP_DIR="/home/ubuntu/$APP_NAME"
Think of these as labels for your project:

APP_NAME → name of your project
GROUP_ID → your “folder” or organization name
APP_DIR → where your project lives on your computer
6️⃣ Create a Maven Web Project
mvn archetype:generate -DgroupId=$GROUP_ID -DartifactId=$APP_NAME -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
Maven creates a new web project using a template.
Imagine it as getting a pre-built Lego set ready to build a web app.
7️⃣ Go into the project folder
cd $APP_DIR
Change your current location to the project folder.
Like walking into the Lego set box to start building.
8️⃣ Create a proper pom.xml
cat > pom.xml <<EOL
...
</project>
EOL
pom.xml is Maven’s instruction book.

It tells Maven:

Project name, version, type (war = web app)
Plugins to use (Jetty plugin to run a web server)
Port number (8080)
We overwrite it with a clean version to avoid errors.

Think of it as a LEGO manual with no missing steps.

9️⃣ Create a fancy index.jsp
mkdir -p src/main/webapp
cat > src/main/webapp/index.jsp << 'EOF'
<html>...
EOF
This is the homepage of your web app.
JSP = Java Server Page → like a dynamic HTML page.
We made it show a big friendly message in the center.
🔟 Open firewall for port 8080
sudo ufw allow 8080/tcp
sudo ufw --force enable
Your EC2 has doors (ports).
8080 is the door for your web app.
This command opens the door so people can see your web app from the internet.
1️⃣1️⃣ Create a systemd service
sudo bash -c "cat > /etc/systemd/system/maven-webapp.service <<EOL
[Unit]
...
EOL"
A systemd service is like a robot helper.
It will start your web app automatically every time the computer boots.
It will also restart the app if it crashes.
1️⃣2️⃣ Reload systemd and start the service
sudo systemctl daemon-reload
sudo systemctl enable maven-webapp.service
sudo systemctl start maven-webapp.service
daemon-reload → tells systemd: “Hey, I added a new robot helper!”
enable → “Make sure this robot starts on boot”
start → “Start the robot now!”
1️⃣3️⃣ Detect EC2 public IP
EC2_PUBLIC_IP=$(curl -s http://169.254.169.254/latest/meta-data/public-ipv4)
EC2 gives your machine a public internet address.
This command finds your EC2 IP so you can visit your web app.
1️⃣4️⃣ Print the final URL
echo "✅ Setup complete!"
echo "👉 Open in browser: http://$EC2_PUBLIC_IP:8080/"
Shows the link to your live web app.
Click it → you’ll see the friendly homepage you created.
Steps you followed after creating the script
Opened the terminal and created maven_setup.sh:
vim maven_setup.sh
Copied the script content into the file.
#!/bin/bash

# Exit immediately on error
set -e

echo "🚀 Updating system..."
sudo apt update -y

echo "☕ Installing Java (OpenJDK 17)..."
sudo apt install -y openjdk-17-jdk

echo "📦 Installing Maven..."
sudo apt install -y maven

echo "✅ Java & Maven Installed:"
java -version
mvn -version

# Variables
APP_NAME="my-webapp"
GROUP_ID="com.example"
APP_DIR="/home/ubuntu/$APP_NAME"

echo "📂 Creating Maven Web Project..."
mvn archetype:generate \
    -DgroupId=$GROUP_ID \
    -DartifactId=$APP_NAME \
    -DarchetypeArtifactId=maven-archetype-webapp \
    -DinteractiveMode=false

cd $APP_DIR

echo "📝 Creating a correct pom.xml..."
cat > pom.xml <<EOL
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>$GROUP_ID</groupId>
  <artifactId>$APP_NAME</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>war</packaging>

  <build>
    <plugins>
      <plugin>
        <groupId>org.eclipse.jetty</groupId>
        <artifactId>jetty-maven-plugin</artifactId>
        <version>9.4.54.v20240208</version>
        <configuration>
          <httpConnector>
            <port>8080</port>
          </httpConnector>
        </configuration>
      </plugin>
    </plugins>
  </build>

</project>
EOL

echo "💻 Creating index.jsp..."
mkdir -p src/main/webapp
cat > src/main/webapp/index.jsp << 'EOF'
<html>
  <body>
    <h1 style="color:red; text-align:center;">
      Hello Maven Web App on AWS EC2 (Port 8080)
      Its all automatic BROOOO!!!!!!!!!!!!
    </h1>
  </body>
</html>
EOF

echo "🛡️ Configuring firewall for port 8080..."
sudo ufw allow 8080/tcp
sudo ufw --force enable

echo "🛠️ Creating systemd service for auto-start..."
sudo bash -c "cat > /etc/systemd/system/maven-webapp.service <<EOL
[Unit]
Description=Maven Jetty Web Application
After=network.target

[Service]
Type=simple
WorkingDirectory=$APP_DIR
ExecStart=/usr/bin/mvn jetty:run
Restart=always
User=ubuntu

[Install]
WantedBy=multi-user.target
EOL"

echo "🔄 Reloading systemd and enabling service..."
sudo systemctl daemon-reload
sudo systemctl enable maven-webapp.service
sudo systemctl start maven-webapp.service

# Detect EC2 public IP
EC2_PUBLIC_IP=$(curl -s http://169.254.169.254/latest/meta-data/public-ipv4)

echo "✅ Setup complete!"
echo "👉 Open in browser: http://$EC2_PUBLIC_IP:8080/"
Saved the file using:
:wq!
Made the script executable:
 chmod +x maven_setup.sh
Ran the script:
 ./maven_setup.sh
Added ports 22, 80, 8080 to Security Group while creating EC2 instance:
22 → SSH access
80 → Optional web access (common HTTP port)
8080 → Jetty web app port
Accessed your app via browser:
 http://<EC2_PUBLIC_IP>:8080/
Sure! Here’s a normal, simple summary of what your maven_setup.sh script does and the steps you followed:

Summary of Maven Web App Setup on Ubuntu EC2
Update system packages

Ensures your Ubuntu system knows about the latest software updates.
Install Java (OpenJDK 17)

Java is required to run Java programs and Maven builds.
Install Maven

Maven is a build tool that manages Java projects, dependencies, and plugins.
Create a Maven web project

Uses a Maven archetype to generate a basic web application structure.
Configure pom.xml

Defines project metadata (groupId, artifactId, version)
Configures the Jetty plugin to run the web server on port 8080
Create index.jsp page

The homepage for the web application with a friendly welcome message.
Configure firewall

Opens port 8080 so the web app is accessible externally.
Create systemd service

Makes the web app run automatically on system boot and restart on failure.
Start the service

Activates the Maven/Jetty web server immediately.
Retrieve EC2 public IP

Determines the public address to access the app in the browser.
Access the web app

Open http://<EC2_PUBLIC_IP>:8080/ to see the running application.
Steps You Followed After Writing the Script
Created maven_setup.sh with vim.
Copied the script content into the file and saved it (:wq!).
Made the script executable: chmod +x maven_setup.sh.
Ran the script: ./maven_setup.sh.
Added ports 22, 80, 8080 to your EC2 Security Group for SSH and web access.
Accessed the app via browser at http://<EC2_PUBLIC_IP>:8080/
