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
This project demonstrates the setup of a **self-hosted GitHub Actions runner** on a **Windows 11 environment**.  
The goal was to configure, test, and secure a CI/CD pipeline running locally — showcasing DevOps automation and workflow management skills.

---

## ⚙️ Setup Steps

### 🏗️ 1. Download & Extract the Runner
```powershell
mkdir C:\actions-runner
cd C:\actions-runner
Invoke-WebRequest -Uri https://github.com/actions/runner/releases/download/v2.329.0/actions-runner-win-x64-2.329.0.zip -OutFile actions-runner.zip
Expand-Archive -Path actions-runner.zip -DestinationPath C:\actions-runner
cd C:\actions-runner

🔗 2. Configure the Runner
.\config.cmd --url https://github.com/Elite-Techs/infinion-devops-assessment --token <your_token_here>

▶️ 3. Start the Runner
.\run.cmd


✅ Once started, the runner connected successfully and began listening for jobs from GitHub.

🚀 Test Workflow

A GitHub Actions workflow (.github/workflows/test-runner.yml) was created to validate the runner setup.

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


🟢 Result: The workflow executed successfully on the local runner — confirming that setup, permissions, and job execution were properly configured.

🔐 Security Considerations
Security Measure	Description
🔒 Local Runner Isolation	Hosted locally (not on public cloud).
🕵️ Token Protection	Temporary GitHub runner token revoked after use.
⚡ Least Privilege	Runner executed with limited admin rights.
🧱 Network Safety	No sensitive environment variables or credentials exposed.
🧠 Challenges & Solutions
Challenge	Solution
❌ pwsh: command not found	Switched from PowerShell Core (pwsh) to native Windows PowerShell.
⚠️ Path Not Found	Ensured directory was created at C:\actions-runner before configuration.
🧩 Workflow Failures	Adjusted YAML syntax, indentation, and shell configuration.
🔁 Iterative Testing	Committed incremental changes and monitored workflow logs via GitHub Actions.
🧭 What I’d Do Differently in Production

🖥️ Host the runner in a dedicated Windows Server VM (or Azure VM).

🧰 Run as a Windows service:

.\svc install
.\svc start


🛡️ Apply firewall and network isolation policies.

🧾 Enable detailed logging, monitoring, and auditing.

🧮 Integrate tools like Dependabot, Trivy, or Snyk for automated security scanning.

🧾 Deliverable

🔗 Repository: Elite-Techs / infinion-devops-assessment

👨‍💻 Submitted by: Prince Richard Osaro

🏁 Summary

This project demonstrates proficiency in:

🧠 GitHub Actions Automation

⚙️ CI/CD Workflow Design

🪟 Windows PowerShell Scripting

🔐 Security-Aware Infrastructure Setup
 
