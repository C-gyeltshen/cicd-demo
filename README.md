# CI/CD Demo Project

## Table of Contents

1. [Introduction to SAST and Snyk](#introduction)
2. [Prerequisites](#prerequisites)
3. [Understanding the Current Project](#understanding-project)
4. [Setting up Snyk Account](#setting-up-snyk)
5. [Configuring GitHub Secrets](#configuring-secrets)
6. [Integrating Snyk with GitHub Actions](#integrating-snyk)
7. [Advanced Snyk Configuration](#advanced-configuration)
8. [Interpreting Snyk Results](#interpreting-results)
9. [Best Practices](#best-practices)
10. [Troubleshooting](#troubleshooting)
11. [Hands-on Exercises](#exercises)

## 1. Introduction to SAST and Snyk {#introduction}

### What is SAST?

Static Application Security Testing (SAST) is a method of computer program debugging that analyzes source code to find security vulnerabilities before the software is deployed. Unlike Dynamic Application Security Testing (DAST), SAST examines code without executing it.

### What is Snyk?

Snyk is a developer-first security platform that helps you find and fix vulnerabilities in your code, dependencies, containers, and infrastructure as code. It provides:

- **Vulnerability scanning** for open source dependencies
- **License compliance** checking
- **Container security** scanning
- **Infrastructure as Code** security
- **Code security** (SAST) analysis

### Why Use Snyk with GitHub Actions?

- **Automated Security**: Runs security checks on every commit/PR
- **Early Detection**: Finds vulnerabilities before they reach production
- **Developer-Friendly**: Integrates seamlessly into existing workflows
- **Continuous Monitoring**: Monitors for new vulnerabilities in existing dependencies

## 2. Prerequisites {#prerequisites}

Before starting this practical, ensure you have:

- [ ] A GitHub account with repository access
- [ ] Basic understanding of Git and GitHub
- [ ] Familiarity with Java and Maven
- [ ] Understanding of CI/CD concepts
- [ ] Access to the `cicd-demo` repository

## 3. Project Setup

### 3.1 Clone the Repository

```bash# Clone the repository
git clone https://github.com/douglasswmcst/cicd-demo.git

# Navigate to the project directory
cd cicd-demo

# Verify the project structure
ls -la
```

### 3.2 Verify the environment

Ensure all the necessary tools are installed:

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

**why install `Apache Maven?`**

Apache Maven is primarily used as a build automation and project management tool, predominantly for Java-based applications. 


## 4. Project Overview
The projectis a `Spring Boot application` with:

- **Framework**: Spring Boot 3.1.2
- **Java Version**: 17
- **Build Tool**: Maven
- **Dependencies**:
  - Spring Web
  - JavaFaker (for generating random data)
  - JaCoCo (for code coverage)


## 4. Setting up Snyk Account

### Step 4.1: Create a Snyk Account

1. **Visit Snyk Website**: Go to [https://snyk.io](https://snyk.io)
2. **Sign Up**: Click "Sign up for free"
3. **Choose Authentication**:
   - Recommended: Sign up with your GitHub account for easier integration
   - Alternative: Use email/password

### Step 4.2: Connect Your GitHub Account

1. **Navigate to Integrations**: In Snyk dashboard, go to "Integrations"
2. **Add GitHub Integration**: Click on "GitHub" integration
3. **Authorize Access**: Allow Snyk to access your repositories
4. **Import Repositories**: Select the repositories you want to monitor

### Step 4.3: Get Your Snyk Token

1. **Access Account Settings**: Click on your profile → "Account settings"
2. **Navigate to API Token**: Go to "Auth Token" section
3. **Generate Token**: Click "Show" to reveal your API token
4. **Copy Token**: Copy the token for later use in GitHub Secrets

⚠️ **Security Note**: Keep your API token secure and never commit it to version control!



