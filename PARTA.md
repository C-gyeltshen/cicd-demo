# Practical 4a: Setting up SAST with SonarCloud in GitHub Actions

## Table of Contents

1. [Introduction to SAST and SonarCloud](#introduction)
2. [Prerequisites](#prerequisites)
3. [Understanding SonarCloud vs Snyk](#comparison)
4. [Setting up SonarCloud Account](#setting-up-sonarcloud)
5. [Configuring GitHub Integration](#configuring-github)
6. [Integrating SonarCloud with GitHub Actions](#integrating-sonarcloud)
7. [Understanding SonarCloud Security Reports](#security-reports)
8. [Continuous Monitoring and Quality Gates](#monitoring)
9. [Best Practices](#best-practices)
10. [Troubleshooting](#troubleshooting)
11. [Hands-on Exercises](#exercises)

## 1. Introduction to SAST and SonarCloud {#introduction}

### What is SAST?

Static Application Security Testing (SAST) analyzes source code to identify security vulnerabilities before deployment. SAST tools examine code structure, data flow, and potential security weaknesses without executing the program.

### What is SonarCloud?

SonarCloud is a cloud-based code quality and security analysis platform that provides:

- **Security Vulnerability Detection**: Identifies security hotspots and vulnerabilities
- **Code Quality Analysis**: Detects bugs, code smells, and maintainability issues
- **Technical Debt Measurement**: Quantifies the effort needed to fix issues
- **Quality Gates**: Automated pass/fail criteria for code quality
- **Continuous Monitoring**: Tracks code quality trends over time

### SonarCloud vs Snyk

While both are SAST tools, they have different focuses:

| Feature | SonarCloud | Snyk |
|---------|------------|------|
| **Primary Focus** | Code quality + Security | Security vulnerabilities |
| **Dependency Scanning** | Limited | Extensive |
| **Code Analysis** | Comprehensive | Security-focused |
| **Quality Metrics** | Extensive | Minimal |
| **Language Support** | 25+ languages | Package managers |
| **Security Hotspots** | Yes | No |
| **Quality Gates** | Yes | Limited |

## 2. Prerequisites {#prerequisites}

Before starting this practical, ensure you have:

- [ ] A GitHub account with repository access
- [ ] Basic understanding of Git and GitHub
- [ ] Familiarity with Java and Maven
- [ ] Understanding of CI/CD concepts
- [ ] Access to the `cicd-demo` repository (from Practical 4)

### Getting Started: Repository Setup

If you haven't already cloned the repository from Practical 4. You may build on the same repo you have previosuly used for practical 4.

```bash
# Clone the repository
git clone https://github.com/douglasswmcst/cicd-demo.git

# Navigate to the project directory
cd cicd-demo

# Verify the project structure
ls -la
```

### Verify Your Environment

```bash
# Check Java version (should be 17 or higher)
java -version

# Check Maven installation
mvn -version

# Test the project builds successfully
mvn clean compile

# Run the tests to ensure everything works
mvn test
```

## 4. Setting up SonarCloud Account {#setting-up-sonarcloud}

### Step 4.1: Create a SonarCloud Account

1. **Visit SonarCloud Website**: Go to [https://sonarcloud.io](https://sonarcloud.io)
2. **Sign Up**: Click "Start now" or "Sign up for free"
3. **Choose Authentication**:
   - **Recommended**: Sign up with your GitHub account
   - This automatically links your repositories

### Step 4.2: Create an Organization

After logging in with GitHub:

1. **Import Organization**: SonarCloud will prompt you to import a GitHub organization
2. **Select Organization**: Choose your GitHub username or organization
3. **Install SonarCloud App**:
   - Click "Install SonarCloud"
   - Select repositories to analyze (choose `cicd-demo`)
   - Approve the installation

### Step 4.3: Create a Project

1. **Analyze New Project**: Click "Analyze new project"
2. **Select Repository**: Choose `cicd-demo` from the list
3. **Set Up Project**: Click "Set Up"
4. **Choose Analysis Method**: Select "With GitHub Actions"

### Step 4.4: Generate SonarCloud Token

1. **Access Account Settings**: Click on your profile → "My Account"
2. **Navigate to Security**: Go to "Security" tab
3. **Generate Token**:
   - Click "Generate Tokens"
   - Name: `cicd-demo-github-actions`
   - Type: Select "User Token"
   - Expiration: Choose appropriate duration (e.g., 90 days)
   - Click "Generate"
4. **Copy Token**: Copy the token immediately (you won't see it again)

⚠️ **Security Note**: Keep your token secure and never commit it to version control!