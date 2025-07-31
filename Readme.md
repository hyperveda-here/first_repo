# Complete Git & GitHub Setup and Push Guide on Windows (PowerShell)

---

## 1. Install Git on Windows

- Download Git for Windows:  
  https://git-scm.com/download/win  
- Install Git with default options.
- Open **Git Bash** or **PowerShell** after installation.

Verify Git installation:

```powershell
git --version


2. Configure Git (One-time setup)
Set your username and email for commits:

powershell
Copy
Edit
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
Verify config:

powershell
Copy
Edit
git config --list
3. Create GitHub Account (if needed)
Sign up at https://github.com

4. Generate SSH Key (in PowerShell)
powershell
Copy
Edit
ssh-keygen -t ed25519 -C "your.email@example.com"
Press Enter to accept default save location.

to see generated ssh key :   cat ~/.ssh/id_ed25519.pub

(Optional) Enter a passphrase or leave empty.

This generates private key (id_ed25519) and public key (id_ed25519.pub) in C:\Users\<User>\.ssh\

5. Start SSH Agent and Add SSH Key (PowerShell)
Run PowerShell as Administrator, then:

powershell
Copy
Edit
Start-Service ssh-agent
Set-Service -Name ssh-agent -StartupType Automatic
Add your SSH private key to the agent:

powershell
Copy
Edit
ssh-add $env:USERPROFILE\.ssh\id_ed25519
6. Add SSH Key to GitHub
Copy the public key content:

powershell
Copy
Edit
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub
Copy the entire output starting with ssh-ed25519 ...

Go to GitHub > Settings > SSH and GPG Keys

Click New SSH key, paste the key, and save.

7. Create a New Repository on GitHub
Go to GitHub and create a new repository (do NOT initialize with README).

Copy the repository URL (SSH recommended):

scss
Copy
Edit
git@github.com:your-username/your-repo.git
8. Initialize Git in Your Local Project Folder
Navigate to your project folder in PowerShell:

powershell
Copy
Edit
cd path\to\your\project
git init
9. Add Remote Repository
Using SSH:

powershell
Copy
Edit
git remote add origin git@github.com:your-username/your-repo.git
10. Stage and Commit Your Files
powershell
Copy
Edit
git add .
git commit -m "Initial commit"
11. Check Your Branch Name and Rename if Needed
Check current branch:

powershell
Copy
Edit
git branch
If the branch is master and you want to use main, rename it:

powershell
Copy
Edit
git branch -M main
12. Push Your Code to GitHub
powershell
Copy
Edit
git push -u origin main
13. Clone Existing Repository (Optional)
powershell
Copy
Edit
git clone git@github.com:your-username/your-repo.git
Useful Git Commands
Command	Description
git status	Show modified files and state
git log	View commit history
git add <file>	Stage specific file
git commit -m "message"	Commit staged changes
git branch	List branches
git branch -M main	Rename current branch to main
git push	Push commits to remote repository
git pull	Pull latest changes from remote
























🎉 You are now set up to use Git and GitHub on Windows with SSH!
