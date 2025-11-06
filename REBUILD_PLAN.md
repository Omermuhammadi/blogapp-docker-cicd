# BlogApp CI/CD Pipeline - Complete Rebuild Plan

## 🚨 **Current Issue:**
- Jenkins EC2 instance (18.212.93.75) is not accessible via SSH or web interface
- Need fresh start to ensure assignment completion and full marks

## 🎯 **Rebuild Strategy (3-4 hours):**

### **Phase 1: Infrastructure Setup (30 minutes)**

#### **1.1 Clean Slate:**
- **Terminate current Jenkins instance** (18.212.93.75)
- **Create new t3.medium Ubuntu 22.04 instance**
- **New security group**: jenkins-sg-v2
  - SSH (22): Your IP
  - HTTP (8080): 0.0.0.0/0 (for webhooks)
  - Custom (3000): Your IP (for app testing)
- **Generate new key pair**: jenkins-v2.pem

#### **1.2 Initial Connection Test:**
- **SSH connection verification**
- **Basic system update**

### **Phase 2: Software Installation (45 minutes)**

#### **2.1 Core Dependencies:**
```bash
# Java 17 (Jenkins requirement)
sudo apt update && sudo apt upgrade -y
sudo apt install openjdk-17-jdk -y

# Jenkins LTS
wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list
sudo apt update && sudo apt install jenkins -y

# Docker & Docker Compose
sudo apt install docker.io docker-compose -y
sudo usermod -aG docker jenkins

# Node.js 20 & Git
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install nodejs git -y
```

#### **2.2 Service Configuration:**
```bash
sudo systemctl enable jenkins docker
sudo systemctl start jenkins docker
```

### **Phase 3: Jenkins Configuration (30 minutes)**

#### **3.1 Web Interface Setup:**
- **Access**: http://[NEW_IP]:8080
- **Initial password**: `sudo cat /var/lib/jenkins/secrets/initialAdminPassword`
- **Install suggested plugins + additional**:
  - GitHub Integration
  - Docker Pipeline
  - Pipeline Stage View

#### **3.2 GitHub Integration:**
- **Credentials**: Add existing GitHub token
- **Test connection** to blogapp-docker-cicd

### **Phase 4: Pipeline Implementation (45 minutes)**

#### **4.1 Create Pipeline Job:**
- **Name**: BlogApp-CICD-Pipeline
- **Type**: Pipeline from SCM
- **Repository**: https://github.com/Omermuhammadi/blogapp-docker-cicd.git
- **Branch**: main
- **Jenkinsfile path**: Jenkinsfile (already exists)

#### **4.2 Test Build:**
- **Manual trigger**: "Build Now"
- **Expected stages**:
  - ✅ Checkout
  - ✅ Environment Setup
  - ✅ Install Dependencies
  - ✅ Run Tests
  - ✅ Build Docker Image
  - ✅ Deploy Application
  - ✅ Health Check

### **Phase 5: Integration & Testing (30 minutes)**

#### **5.1 Update GitHub Webhook:**
- **New URL**: http://[NEW_IP]:8080/github-webhook/
- **Test webhook delivery**

#### **5.2 End-to-End Test:**
- **Make test commit** to trigger pipeline
- **Verify automatic build**
- **Confirm app deployment**: http://[NEW_IP]:3000

### **Phase 6: Documentation & Submission (20 minutes)**

#### **6.1 Add Teacher as Collaborator:**
- **GitHub repository settings**
- **Add teacher's username**

#### **6.2 Create Evidence Documentation:**
- **Screenshots**: Jenkins dashboard, successful builds
- **URLs**: Jenkins, deployed application
- **Test results**: Pipeline logs, application functionality

## 🚀 **Advantages of Fresh Start:**

1. **Clean Environment**: No configuration conflicts
2. **Known Working Setup**: Proven installation steps
3. **Better Documentation**: Step-by-step evidence
4. **Confidence**: Everything will work as expected
5. **Time Efficient**: 3-4 hours vs debugging unknown issues

## 📋 **Pre-Session Preparation:**

### **Before We Start:**
1. **GitHub repository**: ✅ Ready (blogapp-docker-cicd)
2. **Jenkinsfile**: ✅ Ready (with volume mounting)
3. **Docker configuration**: ✅ Ready
4. **Installation commands**: ✅ Prepared

### **What You'll Need:**
- **AWS Console access**
- **GitHub account access**
- **Teacher's GitHub username**
- **3-4 hours focused time**

## 🎯 **Success Criteria:**

- ✅ Jenkins accessible at http://[NEW_IP]:8080
- ✅ Pipeline builds successfully
- ✅ Application deployed at http://[NEW_IP]:3000
- ✅ GitHub webhooks trigger builds automatically
- ✅ Teacher can access repository
- ✅ Complete documentation with evidence

This approach guarantees assignment completion and full marks! 🏆