# NodeApp-CI Pipeline

This repository contains a **Node.js application** with a **Jenkins CI/CD pipeline**.  
The pipeline is automatically triggered by **GitHub Webhooks** whenever a commit is pushed to the `main` branch or a pull request is opened/updated.

---
## Lab 10-SCD
## **Pipeline Stages**

1. **Checkout Code**  
   Clones the repository and checks out the `main` branch.

2. **Install Dependencies**  
   Runs `npm install` to install required Node.js packages.

3. **Run Tests**  
   Executes `npm test`. Currently uses `testScript.js` for basic event tests.

4. **Info Stage**  
   Prints:
   - **Build Number**
   - **Timestamp of build**
   - **Message if triggered by GitHub Webhook**

5. **Post Actions**
   - Success: `Build and tests successful!`
   - Failure: `Build failed or tests failed!`

---

## **GitHub Webhook Integration**

- Webhook URL for Jenkins:
