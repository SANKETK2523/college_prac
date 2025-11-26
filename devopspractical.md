# GPT Command which i had given 
 think like i am 5 years old like wise give me explantion like that so when come again to visit my github readme file i will know the things which i had done today
---

# 🧑‍💻 **Practical 1: Creating a Git Repository and Pushing to GitHub**

## 🧠 **What I Learned**

Today, I learned how to:

1. Create a new Git repository on my local computer.
2. Connect it to a remote GitHub repository.
3. Add and commit files, then push them to GitHub.
4. Understand the purpose of each Git command used in the process.

---
## ✅ **Steps I Followed**

### 🚀 **1. Initialize a New Git Repository**

```bash
git init
```

📁 This tells Git:

> “Hey! Start tracking changes in this folder now.”

A hidden `.git` folder is created — it stores all version history.

---

### 🧾 **2. Create a New File**

```bash
echo "I am Sai" >> sai.txt
```

This creates a new file named **sai.txt** and adds the text inside it.

---

### 🌿 **3. Rename Default Branch to `main`**

```bash
git branch -M main
```

This ensures your default branch is **main** (not master).

---

### 🔗 **4. Add Remote Repository (GitHub Link)**

```bash
git remote add origin https://github.com/your-username/your-repo.git
```

💡 Replace `your-username` and `your-repo` with your actual GitHub username and repository name.

> “This is where I’ll send my project files — to this GitHub repo.”

---

### 🔍 **5. Verify the Remote Repository**

```bash
git remote -v
```

Expected output:

```
origin  https://github.com/your-username/your-repo.git (fetch)
origin  https://github.com/your-username/your-repo.git (push)
```

This confirms your remote connection is set up correctly.

---

### 🗃️ **6. Add All Files to the Staging Area**

```bash
git add .
```

This tells Git:

> “Include all modified and new files for the next commit.”

---

### 🔎 **7. Check Git Status**

```bash
git status
```

You’ll see:

* Current branch name (main)
* Which files are staged
* Which files are untracked

---

### 💾 **8. Commit the Changes**

```bash
git commit -m "Added sai.txt file with introduction text"
```

This creates a **snapshot** of your project with a message explaining what changed.

📝 Always use meaningful commit messages!

---

### 📤 **9. Push Changes to GitHub**

```bash
git push -u origin main
```

### 10 If error then execute this command

```bash
git pull origin main --allow-unrelated-histories
```
```
:q!
```
then execute these commands
```bash
git add .
git commit -m "Merged remote and local histories"
git push origin main
```


> “Send my committed changes to GitHub’s `main` branch.”

💡 The `-u` flag links your local `main` branch with the remote one.
Next time, you can simply run `git push`.

---

## 💡 **Tips for Future Me**

✅ Run `git init` only once per project.
✅ Use `git status` often to stay aware of what’s happening.
✅ Always write clear and descriptive commit messages.
✅ Make sure your GitHub remote is added only once.
✅ Use `git branch -M main` if your branch name is still `master`.

---

## 🧾 **Final Summary of Commands**

```bash
git init
echo "I am Sai" >> sai.txt
git branch -M main
git remote add origin https://github.com/your-username/your-repo.git
git remote -v
git add .
git status
git commit -m "Added sai.txt file with introduction text"
git push -u origin main
```

---

----------------------------------------------------------------------------------------------------------------------------------------
# 🧑‍💻 Practical 2: Cloning, Branching, Pushing, and Pull Requests on GitHub (updated flow)

## 🧠 What I Learned

Today, I learned how to:

1. **Clone** a GitHub repository to my computer.
2. **Create a new branch first** (work on feature branch locally).
3. **Create or edit files** on that branch.
4. **Add, commit, and push** the branch to GitHub.
5. **Open a Pull Request** to merge into `main`.
6. **Sync changes** from GitHub to my local `main`.
7. **Clear old login information** using Credential Manager.

---

## 🔧 Steps I Did (modified order: create feature branch right after cloning)

### ✅ 1. Clone the Repository from GitHub

```bash
git clone https://github.com/PhapaleSai/College_repo.git
```

👉 Now a folder named `College_repo` is on your computer.

---

### ✅ 2. Enter the Repository

```bash
cd College_repo/
ls
```

This shows the files and folders inside the project.

---

### ✅ 3. Create a New Branch (do this immediately after cloning)

Create and switch to a new branch called `feature`:

```bash
git checkout -b feature
```

🔄 This creates `feature` and checks it out so you’re working on that branch.

---

### ✅ 4. Create or Edit a File on the `feature` Branch

Option A — Use `vim`:

```bash
vim sai.txt
# press i to insert, type your text, Esc, :wq, Enter to save and quit
```

Option B — Use echo:

```bash
echo "hello i am sai" > sai.txt
```

---

### ✅ 5. Check Git Status

```bash
git status
```

See which files are untracked or modified on the `feature` branch. 

---

### ✅ 6. Add the File to Staging

```bash
git add sai.txt
# or to add everything: git add .
```

---

### ✅ 7. Commit Your Changes

```bash
git commit -m "Added sai.txt with introduction"
```

This saves a snapshot on the `feature` branch.

---

### ✅ 8. (Optional) Ensure Remote Is Set

If remote isn't set (usually isn't needed after clone), add it:

```bash
git remote add origin https://github.com/PhapaleSai/College_repo.git
git remote -v
```

---

### ✅ 9. Push the `feature` Branch to GitHub

```bash
git push origin feature
```

🚀 Your `feature` branch and commits are now on GitHub.

---

### ✅ 10. Create a Pull Request (on GitHub)

1. Go to: `https://github.com/PhapaleSai/College_repo`
2. Click **Compare & pull request** for the `feature` branch.
3. Add title/description (e.g., "Added sai.txt").
4. Click **Create Pull Request**.
5. When ready, click **Merge pull request** → **Confirm merge**.

🎉 Your changes are now merged into `main` on GitHub.

---

### ✅ 11. Sync Changes from GitHub to Your Local `main`

Switch back to local `main` and pull:

```bash
git checkout main
git pull origin main
```

This updates your local `main` with the merged changes.

---

### ✅ 12. Important Note: Credential Manager (Windows)

If the wrong GitHub credentials are cached:

1. Open **Windows Search** → type **Credential Manager**.
2. Open it → **Windows Credentials**.
3. Remove any entries for `git:https://github.com`.
4. Next push/pull will prompt you for the correct login.

---

## 📌 Summary of Commands (updated order)

```bash
git clone https://github.com/PhapaleSai/College_repo.git
cd College_repo/
git checkout -b feature        # create & switch to feature branch first
# create/edit file:
vim sai.txt                    # or: echo "hello i am sai" > sai.txt
git status
git add sai.txt                # or git add .
git commit -m "Added sai.txt with introduction"
git remote add origin <repo-url>   # only if needed
git remote -v                   # optional check
git push origin feature
# create PR on GitHub, merge into main
git checkout main
git pull origin main
```

---

## 💡 Tips (reminders)

* Creating the branch immediately after cloning keeps your changes isolated and makes collaboration cleaner.
* Use `git status` often.
* Use descriptive commit messages.
* If you need to update the feature branch after creating the PR, make more commits on `feature` and `git push origin feature` — the PR updates automatically.

---

### 🧑‍💻 Practical 3: Cloning, Branching, Pushing, and Pull Requests on GitLab

### 🧠 **What I Learned**

Today, I learned how to:

* Clone a GitLab repository to my computer.
* Make changes to files.
* Create a new branch to work separately.
* Push changes to GitLab from a new branch.
* Collaborate using Merge Requests on GitLab.
* Sync changes from GitLab to my computer.
* Correct old login information in Git's credential manager.

### 🔧 **Steps I Did in Order**

#### ✅ 1. **Cloned the Repository from GitLab**

This brings the GitLab project from the internet to my computer.

```bash
git clone https://gitlab.com/sai_phapale-group/Sai_Phapale-project.git
```

👉 Now a folder named `Sai_Phapale-project` is on my computer.

#### ✅ 2. **Checked What's Inside**

```bash
ls
cd Sai_Phapale-project/
ls
```

📁 This shows me all the files inside the project.

#### ✅ 3. **Created or Edited a File**

I made or updated a file called `sai.txt` using the echo command.

```bash
echo "Hello World" > sai.txt
```

👉 This creates a new file with the text "Hello World" inside it.

#### ✅ 4. **Checked Git Status**

This shows what files I changed or added.

```bash
git status
```

#### ✅ 5. **Committed My Changes**

But wait! I forgot to add the file to the staging area. 😅 So I fixed that:

```bash
git add sai.txt
```

Then I saved my work with a message:

```bash
git commit -m "Added new file sai.txt"
```

📝 This creates a snapshot of my changes.

#### ✅ 6. **Created a New Branch**

I wanted to work on a separate line called `feature`.

```bash
git branch feature
git checkout feature
```

🔄 Now I’m working in the `feature` branch.

#### ✅ 7. **Added Remote Link (If not already added)**

Just to make sure Git knows where my GitLab repo is:

```bash
git remote add origin https://gitlab.com/sai_phapale-group/Sai_Phapale-project.git
git remote -v
```

This shows the link to GitLab is working. 👍

#### ✅ 8. **Pushed My Changes to GitLab**

I sent my changes from my local `feature` branch to GitLab.

```bash
git push origin feature
```

🚀 Now my changes are on GitLab, under the `feature` branch.

#### ✅ 9. **Created a Merge Request (on GitLab)**

Now it’s time to ask GitLab to bring my `feature` changes into the main project.
🖱️ Go to: [https://gitlab.com/sai\_phapale-group/Sai\_Phapale-project](https://gitlab.com/sai_phapale-group/Sai_Phapale-project)

Then:

1. Click the “Merge Requests” tab on the left sidebar.
2. Click the "New Merge Request" button.
3. Select the `feature` branch and the `main` branch (or whichever branch you want to merge into).
4. Write a title and description (e.g., "Added new file sai.txt").
5. Click “Submit Merge Request”.
6. If you're ready to bring the changes into `main`, click “Merge”.
7. Confirm by clicking “Merge” again.

🎉 Done! Your changes are now part of `main`.

#### ✅ 10. **Sync Changes from GitLab to My Computer**

First, switch back to the `main` branch on your local machine (master) branch because in GitLab we have master branch instead of main:

```bash
git checkout master
```

Then get the latest changes from GitLab:

```bash
git pull origin master
```

🌐 This updates your local `main` branch with everything from GitLab.

#### ✅ 11. **Important Note: Credential Manager**

If someone else was logged in before, you might see their GitLab login.

To fix this:

1. Go to **Windows Search** > type **Credential Manager**.
2. Open it.
3. Go to **Windows Credentials**.
4. Find anything that says `git:https://gitlab.com` and remove it.
5. Next time you push or pull, Git will ask for your GitLab login.

🔐 This keeps your GitLab account safe and correct.

---

### 📌 **Summary of Commands Used**

```bash
git clone <repo-url>
ls
cd Sai_Phapale-project/
echo "Hello World" > sai.txt
git status
git add sai.txt
git commit -m "Added new file sai.txt"
git branch feature
git checkout feature
git remote add origin <repo-url>
git remote -v
git push origin feature
git checkout main
git pull origin main
```
---

# 🧑‍💻 Practical 4: Cloning, Branching, Pushing, and Pull Requests on Bitbucket

---

## 🧠 What I Learned

Today, I learned how to:

* **Clone** a repository from Bitbucket.
* **Create a new file**, stage it, and commit it.
* **Create and switch to a feature branch**.
* **Push my branch** to Bitbucket.
* **Make a Pull Request (PR)** on the Bitbucket website.
* **Merge my feature branch into the main branch**.
* **Update my local main branch** after merging.

---

## ✅ Steps I Followed

### 🚀 1. Clone a Repository from Bitbucket

```bash
git clone https://college_demo-admin@bitbucket.org/college_demo/practice_check.git
```

📁 This tells Git:
“Please make a copy of this repo on my computer.”

---

### 📂 2. Go Inside the Repo Folder

```bash
cd practice_check/
ls
```

---

### 📄 3. Create a New File

```bash
echo "i am sai" > sai.txt
ls
```

This makes a new file named **sai.txt** with the text *i am sai*.

---

### 💾 4. Add and Commit the File

```bash
git add sai.txt
git commit -m "the file is added"
```

This saves my file into Git’s history.

---

### 🌱 5. Create and Switch to a Feature Branch

```bash
git checkout -b feature
```

💡 This makes a new branch called **feature** and moves me into it.

---

### 🌍 6. Push the Feature Branch to Bitbucket

```bash
git push origin feature
```

This uploads the **feature** branch (with sai.txt) to Bitbucket.

---

### 🖱️ 7. Create a Pull Request on Bitbucket Website

1. Open [bitbucket.org](https://bitbucket.org).
2. Log in to your account.
3. Go to your repository → **practice\_check**.
4. On the left menu, click **Pull requests**.
5. Click the blue **Create pull request** button (top-right).
6. Select:

   * **Source branch** → `feature`.
   * **Destination branch** → `main`.
7. Add a title → `"Added sai.txt file"`.
8. (Optional) Add a description.
9. Click the green **Create pull request** button.

---

### 👀 8. Review and Merge in Bitbucket

1. On the Pull Request screen, check the changes.
2. If all looks good, click **Merge** (top-right).
3. Now Bitbucket combines your `feature` branch into `main`. 🎉

---

### 🔙 9. Update Your Local Main Branch

```bash
git checkout main
git pull origin main
ls
```

Now my **main** branch also has **sai.txt**.

---

## 🧾 Summary of Commands Used

```
git clone <repo-url>
cd practice_check/
echo "i am sai" > sai.txt
git add sai.txt
git commit -m "the file is added"
git checkout -b feature
git push origin feature
git checkout main
git pull origin main
```

---

## 💡 Tips for Future Me

* Always create a branch before making new changes.
* Push your branch **before** making a Pull Request.
* On Bitbucket: **Pull requests → Create pull request → feature → main → Merge**.
* Write short and clear commit + PR messages.
* After merging, always run `git pull origin main` so your local copy is updated. 

---


Perfect 👍 Let’s extend your **super simple README** with **AWS EC2 steps included**, so you’ll remember not just Docker, but also **how you set up your cloud computer**.

Here’s your final **README.md**:

---

# Assignemnt 6 Exploring Containerization and Application Deployment with Docker 
🐳 My First Docker Project (Apache Web Server on AWS EC2)

Hi future me 👋,
This is what I did today step by step. Read it like a story so you don’t forget 🚀

---

## 🌍 What I wanted to do

* Make a tiny website that says **“Hello, Docker!”**
* Put it inside a **Docker container** with **Apache web server**
* Run it on my **AWS EC2 instance** (cloud computer)
* Open it in a browser at `http://<my-ec2-ip>:8080`

---

## 🧰 Tools I used

* **AWS EC2** (Ubuntu machine = my cloud laptop 💻☁️)
* **Docker** (to make containers 🐳)
* **Apache (httpd)** (to serve my web page 🍽️)

---

## ☁️ Steps for AWS EC2 Setup

1. **Create EC2 Instance**

   * Chose **Ubuntu 22.04** (free tier t2.micro).
   * Created **key pair (.pem file)** to connect.
   * In **Security Group**, opened ports:

     * **22 (SSH)** → so I can connect
     * **8080 (TCP)** → so I can see my website

2. **Connect to EC2** (from my computer terminal):

   ```bash
   ssh -i mykey.pem ubuntu@<EC2-Public-IP>
   ```

3. **Update EC2 and Install Docker**:

   ```bash
   sudo apt update
   sudo apt install -y docker.io
   sudo systemctl start docker
   sudo systemctl enable docker
   sudo usermod -aG docker ubuntu
   ```

---

## 👣 Steps I took for Docker Project (like a recipe)

1. **Make a folder for my project**

   ```bash
   mkdir mydockerapp
   cd mydockerapp
   ```

2. **Create a simple web page**

   ```bash
   echo "<h1>Hello, Docker</h1>" > index.html
   ```

3. **Create a Dockerfile**

   ```dockerfile
   vim Dockerfile
   ```

   ```
   FROM httpd:2.4
   COPY index.html /usr/local/apache2/htdocs/
   ```
   ```
   :wq! ((save the file)
   ```

   👉 This means:

   * “Hey Docker, use Apache as base”
   * “Copy my `index.html` inside Apache’s web folder”

4. **Build my Docker image**

   ```bash
   sudo docker build -t my-apache-server .
   ```

5. **Run my container**

   ```bash
   sudo docker run -p 8080:80 -d my-apache-server
   ```

   👉 This means:

   * Port 80 inside container → Port 8080 on EC2
   * Run in background mode

6. **Check it’s running**

   ```bash
   sudo docker ps
   ```

7. **Open in browser**

   ```
   http://<EC2-Public-IP>:8080
   ```

   🎉 I saw my page: **Hello, Docker!**

---

## 🧹 Cleanup (if needed)

* Stop the container:

  ```bash
  sudo docker stop <container_id>
  ```
* Remove container:

  ```bash
  sudo docker rm <container_id>
  ```
* Remove image:

  ```bash
  sudo docker rmi my-apache-server
  ```

---

## 🎯 What I learned

* **EC2** = my computer in the cloud ☁️
* **Docker** = magic box for apps 🪄
* **Apache** = waiter who serves my web page 🍽️
* **Port mapping** = “Hey outside world, talk to my container through this door 🚪”

---

## 📘 Quick Docker Commands (cheat sheet for future me)

* See running containers:

  ```bash
  docker ps
  ```
* See all containers (even stopped ones):

  ```bash
  docker ps -a
  ```
* List all images:

  ```bash
  docker images
  ```
* Stop container:

  ```bash
  docker stop <id>
  ```
* Remove container:

  ```bash
  docker rm <id>
  ```
* Remove image:

  ```bash
  docker rmi <image-name>
  ```
---

Assignemnt 8 - Practical Maven Assignment 
---

## **Step-by-Step Explanation of `maven_setup.sh`**

### **1️⃣ Update the system**

```bash
sudo apt update -y
```

* Think of this as **telling your Ubuntu computer to check for the latest toy updates**.
* `apt update` makes sure your computer knows about the newest software packages.

---

### **2️⃣ Install Java**

```bash
sudo apt install -y openjdk-17-jdk
```

* Java is like a **magic engine** that can run programs written in Java.
* We installed **OpenJDK 17**, a free version of Java.
* `-y` means “Yes, I want to install it” without asking every time.

---

### **3️⃣ Install Maven**

```bash
sudo apt install -y maven
```

* Maven is like a **recipe manager for Java projects**.
* It knows how to **build projects, download libraries, and run web apps**.

---

### **4️⃣ Check if Java & Maven work**

```bash
java -version
mvn -version
```

* This is like **testing if our magic engine and recipe manager are ready**.
* It prints the version so you know everything installed correctly.

---

### **5️⃣ Set some variables**

```bash
APP_NAME="my-webapp"
GROUP_ID="com.example"
APP_DIR="/home/ubuntu/$APP_NAME"
```

* Think of these as **labels for your project**:

  * `APP_NAME` → name of your project
  * `GROUP_ID` → your “folder” or organization name
  * `APP_DIR` → where your project lives on your computer

---

### **6️⃣ Create a Maven Web Project**

```bash
mvn archetype:generate -DgroupId=$GROUP_ID -DartifactId=$APP_NAME -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
```

* Maven creates a **new web project** using a template.
* Imagine it as **getting a pre-built Lego set ready to build a web app**.

---

### **7️⃣ Go into the project folder**

```bash
cd $APP_DIR
```

* Change your current location to the project folder.
* Like **walking into the Lego set box** to start building.

---

### **8️⃣ Create a proper `pom.xml`**

```bash
cat > pom.xml <<EOL
...
</project>
EOL
```

* `pom.xml` is Maven’s **instruction book**.
* It tells Maven:

  * Project name, version, type (war = web app)
  * Plugins to use (Jetty plugin to run a web server)
  * Port number (8080)
* We **overwrite it** with a clean version to avoid errors.
* Think of it as **a LEGO manual with no missing steps**.

---

### **9️⃣ Create a fancy `index.jsp`**

```bash
mkdir -p src/main/webapp
cat > src/main/webapp/index.jsp << 'EOF'
<html>...
EOF
```

* This is the **homepage of your web app**.
* JSP = Java Server Page → **like a dynamic HTML page**.
* We made it show a big friendly message in the center.

---

### **🔟 Open firewall for port 8080**

```bash
sudo ufw allow 8080/tcp
sudo ufw --force enable
```

* Your EC2 has **doors (ports)**.
* 8080 is the **door for your web app**.
* This command **opens the door** so people can see your web app from the internet.

---

### **1️⃣1️⃣ Create a systemd service**

```bash
sudo bash -c "cat > /etc/systemd/system/maven-webapp.service <<EOL
[Unit]
...
EOL"
```

* A **systemd service** is like a **robot helper**.
* It will **start your web app automatically every time the computer boots**.
* It will also **restart the app if it crashes**.

---

### **1️⃣2️⃣ Reload systemd and start the service**

```bash
sudo systemctl daemon-reload
sudo systemctl enable maven-webapp.service
sudo systemctl start maven-webapp.service
```

* `daemon-reload` → tells systemd: “Hey, I added a new robot helper!”
* `enable` → “Make sure this robot starts on boot”
* `start` → “Start the robot now!”

---

### **1️⃣3️⃣ Detect EC2 public IP**

```bash
EC2_PUBLIC_IP=$(curl -s http://169.254.169.254/latest/meta-data/public-ipv4)
```

* EC2 gives your machine a **public internet address**.
* This command **finds your EC2 IP** so you can visit your web app.

---

### **1️⃣4️⃣ Print the final URL**

```bash
echo "✅ Setup complete!"
echo "👉 Open in browser: http://$EC2_PUBLIC_IP:8080/"
```

* Shows the **link to your live web app**.
* Click it → you’ll see the friendly homepage you created.

---

## **Steps you followed after creating the script**

1. Opened the terminal and created `maven_setup.sh`:

```bash
vim maven_setup.sh
```

2. **Copied the script content** into the file.
```bash
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

```

4. **Saved the file** using:

```
:wq!
```

4. **Made the script executable**:

```bash
 chmod +x maven_setup.sh
```

5. **Ran the script**:

```bash
 ./maven_setup.sh
```

6. **Added ports 22, 80, 8080 to Security Group** while creating EC2 instance:

* 22 → SSH access
* 80 → Optional web access (common HTTP port)
* 8080 → Jetty web app port

7. **Accessed your app** via browser:

```
 http://<EC2_PUBLIC_IP>:8080/
```

---

Sure! Here’s a **normal, simple summary** of what your `maven_setup.sh` script does and the steps you followed:

---

### **Summary of Maven Web App Setup on Ubuntu EC2**

1. **Update system packages**

   * Ensures your Ubuntu system knows about the latest software updates.

2. **Install Java (OpenJDK 17)**

   * Java is required to run Java programs and Maven builds.

3. **Install Maven**

   * Maven is a build tool that manages Java projects, dependencies, and plugins.

4. **Create a Maven web project**

   * Uses a Maven archetype to generate a basic web application structure.

5. **Configure `pom.xml`**

   * Defines project metadata (groupId, artifactId, version)
   * Configures the **Jetty plugin** to run the web server on port 8080

6. **Create `index.jsp` page**

   * The homepage for the web application with a friendly welcome message.

7. **Configure firewall**

   * Opens port 8080 so the web app is accessible externally.

8. **Create systemd service**

   * Makes the web app run automatically on system boot and restart on failure.

9. **Start the service**

   * Activates the Maven/Jetty web server immediately.

10. **Retrieve EC2 public IP**

    * Determines the public address to access the app in the browser.

11. **Access the web app**

    * Open `http://<EC2_PUBLIC_IP>:8080/` to see the running application.

---

### **Steps You Followed After Writing the Script**

1. Created `maven_setup.sh` with `vim`.
2. Copied the script content into the file and saved it (`:wq!`).
3. Made the script executable: `chmod +x maven_setup.sh`.
4. Ran the script: `./maven_setup.sh`.
5. Added **ports 22, 80, 8080** to your EC2 Security Group for SSH and web access.
6. Accessed the app via browser at `http://<EC2_PUBLIC_IP>:8080/`.

---


