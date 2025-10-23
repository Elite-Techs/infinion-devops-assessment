
<h1 align="center">🚀 Infinion DevOps Assessment – Self-Hosted GitHub Actions Runner</h1>

<p align="center">
  <b>By Prince Richard Osaro</b>  
  <br/>
  <a href="https://github.com/Elite-Techs">GitHub</a> • 
  <a href="https://linkedin.com/in/prince-richard-o">LinkedIn</a> • 
  <a href="mailto:princerichard547@gmail.com">Email</a>
</p>

---

## 🧩 Overview
This project demonstrates the setup of a **self-hosted GitHub Actions runner** on a Windows 11 environment.  
The goal was to configure, test, and secure a CI/CD pipeline running locally — showcasing DevOps automation and workflow orchestration skills.

---

## ⚙️ Setup Steps

### 🏗️ 1. Download & Extract the Runner
```powershell
mkdir C:\actions-runner
cd C:\actions-runner
Invoke-WebRequest -Uri https://github.com/actions/runner/releases/download/v2.329.0/actions-runner-win-x64-2.329.0.zip -OutFile actions-runner.zip
Expand-Archive -Path actions-runner.zip -DestinationPath C:\actions-runner
cd C:\actions-runner
```

### 🔗 2. Configure the Runner
```powershell
.\config.cmd --url https://github.com/Elite-Techs/infinion-devops-assessment --token <your_token_here>
```

### ▶️ 3. Start the Runner
```powershell
.\run.cmd
```

✅ Once started, the runner connected successfully and began listening for jobs from GitHub.

---

## 🚀 Test Workflow

A GitHub Actions workflow (`.github/workflows/test-runner.yml`) was created to validate the runner setup:

```yaml
name: Test Windows PowerShell Runner
on:
  push:
    branches: [ main ]

jobs:
  test-runner:
    runs-on: self-hosted
    steps:
      - uses: actions/checkout@v3

      - name: Verify PowerShell
        shell: powershell
        run: |
          Write-Host "✅ PowerShell is working on the self-hosted Windows runner."
          Get-Date
          Get-Location

      - name: Run basic command
        shell: powershell
        run: |
          Write-Host "Testing environment..."
          $env:COMPUTERNAME
          Get-Service | Select-Object -First 5
```

🟢 Result: The workflow executed successfully — confirming that the setup, permissions, and job execution pipeline were properly configured.

---

## 🔐 Security Considerations

| Security Measure      | Description |
|----------------------|-------------|
| 🔒 Local Runner Isolation | Runner hosted locally (not on the public cloud). |
| 🕵️ Token Protection      | GitHub runner token was temporary and revoked after configuration. |
| ⚡ Least Privilege       | Runner was run without full admin rights to limit scope. |
| 🧱 Network Safety        | No sensitive environment variables or credentials exposed. |

---

## 🧠 Challenges & Solutions

| Challenge                  | Solution |
|----------------------------|---------|
| ❌ pwsh: command not found | Switched from `pwsh` to native Windows PowerShell |
| ⚠️ Path Not Found          | Ensured directory `C:\actions-runner` was created before configuration |
| 🧩 Workflow Failures       | Adjusted YAML indentation and shell syntax |
| 🔁 Testing Iterations       | Pushed iterative commits and monitored workflow logs in GitHub Actions |

---

## 🧭 What I’d Do Differently in Production

- Host the runner in a dedicated Windows Server VM or Azure VM.  
- Configure the runner as a Windows Service for continuous availability:

```powershell
.\svc install
.\svc start
```

- Apply firewall rules and network isolation.  
- Enable centralized logging, monitoring, and alerting.  
- Integrate security scanning tools like Dependabot, Trivy, or Snyk.  

---

## 📸 Screenshots

Visual reference for setup, configuration, and workflow execution:  

[View Screenshots & Details](Screenshots/README.md)

> This folder contains all key visuals with explanations for each step.

---

## 🧾 Deliverables

🔗 Repository: [https://github.com/Elite-Techs/infinion-devops-assessment](https://github.com/Elite-Techs/infinion-devops-assessment)

👨‍💻 Submitted by: Prince Richard Osaro

---

## 🏁 Summary

This project demonstrates proficiency in:

- 🧠 GitHub Actions Automation  
- ⚙️ DevOps CI/CD Workflow Design  
- 🪟 Windows PowerShell Scripting  
- 🔐 Security-Aware Infrastructure Setup  

<p align="center">
  <b>⭐ If you found this project helpful, please give it a star!</b>  
  <br/>💬 Open to DevOps, IT Support, and Cybersecurity collaborations.
</p>
