# 🚀 Create Server and Deploy Application on DigitalOcean

This demo project demonstrates how to set up and configure a Linux server on DigitalOcean, create a secure user, and deploy a Java application built with Gradle to the remote server. It is part of **Module 5 - Cloud & Infrastructure as a Service Basics** from the TechWorld with Nana DevOps Bootcamp.

---

## 🛠️ Technologies Used

- DigitalOcean Droplet (Ubuntu Linux)
- Java (JDK 17 or higher)
- Gradle Build Tool
- IntelliJ IDEA (for local development)
- SSH & SCP (for secure remote access and file transfer)

---

## 📆 Project Description

### ✅ Key Tasks Completed:

1. **Create and Configure Droplet**

   - Used DigitalOcean to create a new Ubuntu server (Droplet)
   - Enabled SSH access and assigned a static IP address

2. **Create a New Linux User**

   - Followed security best practices to avoid using root
   - Created a new user with `adduser devops`
   - Granted sudo privileges
   - Configured SSH access for the new user

3. **Install Java & Gradle on Droplet**

   - Installed JDK and verified with `java -version`
   - Installed Gradle and verified with `gradle -v`

4. **Deploy Java Gradle Application**

   - Cloned or transferred `java-react-example` project to Droplet
   - Navigated to the project directory and ran:

     ```bash
     ./gradlew build
     java -jar build/libs/<your-jar-file>.jar
     ```

   - Application ran successfully and could be accessed if exposed over a public port

---

## 🔧 Setup Instructions

### 1. Connect to Droplet

```bash
ssh root@<your_droplet_ip>
```

### 2. Create a New User

```bash
adduser devops
usermod -aG sudo devops
```

### 3. Configure SSH for New User

```bash
rsync --archive --chown=devops:devops ~/.ssh /home/devops
```

### 4. Install Java & Gradle

```bash
apt update && apt install openjdk-17-jdk -y
sdk install gradle  # if using SDKMAN, or manual install otherwise
```

### 5. Transfer Project & Deploy

```bash
scp -r java-react-example devops@<your_droplet_ip>:/home/devops
ssh devops@<your_droplet_ip>
cd java-react-example
./gradlew build
java -jar build/libs/<your-jar-file>.jar
```

---

## 🚀 Outcome

- Successfully deployed a locally developed Java application on a remote Linux server
- Reinforced understanding of infrastructure provisioning, Linux security best practices, and basic deployment operations

---

## 📊 Repository Structure (if applicable)

```
java-react-example/
├── build.gradle
├── settings.gradle
├── src/
├── README.md
```

---

## 🛌 Notes

- Make sure port 8080 (or the one your app uses) is open in DigitalOcean's firewall settings
- Always use non-root users in production for running services
