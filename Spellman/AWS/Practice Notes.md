# Obsidian Git Plugin — Windows Setup Guide (Step-by-Step)  
  
This is a **Windows-specific walkthrough** for setting up the **Obsidian Git** plugin. It assumes you want to manage your Obsidian vault with Git and sync to a GitHub, GitLab, or Bitbucket repository.  
  
---  
  
## 0) Prerequisites  
- [ ] Windows 10 or 11  
- [ ] **Obsidian** is installed  
- [ ] **Git for Windows** is installed  
- [ ] You have a **GitHub/GitLab/Bitbucket** account  
- [ ] You know whether you’ll use **HTTPS** (with a token) or **SSH keys**  
  
## 1) Install Git for Windows  
1. Go to [https://git-scm.com/download/win](https://git-scm.com/download/win)  
2. Run the installer and **accept all defaults** — especially these options:  
   - ✅ *Git from the command line and also from 3rd-party software*  
   - ✅ *Use bundled OpenSSH*  
   - ✅ *Use Git Credential Manager* (saves your login)  
3. After installation, open **PowerShell** or **Command Prompt** and verify:  
```powershell  
git --version  
```

## 2) Create or Open an Obsidian Vault  
1. Launch **Obsidian**.  
2. Either create a **new vault** or open an existing one.  
3. Right-click inside the vault folder → **Open in Terminal**.  
   - You can also use PowerShell and navigate manually:  
```powershell  
cd "C:\Users\YourName\Documents\ObsidianVault"  
```

3) Initialize Git in the Vault  
4. In the vault’s terminal:  
```powershell  
git init  
```  
2. Create a `.gitignore` file to exclude temporary or layout files:  
```text  
# .gitignore  
.obsidian/workspace.json  
.obsidian/workspace-mobile.json  
.obsidian/appearance.json  
.DS_Store  
Thumbs.db  
.trash/  
```  
3. Configure Git line endings to avoid weird diffs:  
```powershell  
git config core.autocrlf true  
```


 4) Create & Link a Remote Repository  
**On GitHub (or similar):**  
5. Log in → Create a **new empty repository** (no README/license yet).  
6. Copy the repo’s **HTTPS** or **SSH** URL.  
  
**In your vault folder terminal:**  
```powershell  
git remote add origin <REMOTE_URL>  
git branch -M main  
```  
  
**Initial commit & push:**  
```powershell  
git add .  
git commit -m "Initial Obsidian vault setup"  
git push -u origin main  
```  
  
> 🔐 **If using HTTPS**, use your **Personal Access Token** instead of your GitHub password.  
>  
> 💡 **If using SSH**, make sure you’ve added your SSH key to GitHub and run:  
> ```powershell  
> ssh -T git@github.com  
> ```  
> to verify it’s working.


 5) Install the Obsidian Git Plugin  
6. In Obsidian → ⚙️ **Settings** → **Community plugins**.  
7. Turn off **Restricted Mode**.  
8. Click **Browse** → search **Obsidian Git**.  
9. Click **Install**, then **Enable**.

## 6) Configure Plugin Settings (Windows Recommended)  
In **Settings → Community plugins → Obsidian Git**:  
  
| Setting | Recommended Value | Notes |  
|----------|------------------|--------|  
| **Commit message** | `vault backup: {{date}}` | Auto timestamps commits |  
| **Auto commit** | ✅ Enabled (every 10–15 min) | Keeps vault backed up |  
| **Auto push** | ✅ Enabled | Syncs automatically |  
| **Pull on startup** | ✅ Enabled | Always up-to-date on open |  
| **Auto pull before push** | ✅ Enabled | Prevents merge errors |  
| **Show status bar** | ✅ Enabled | See Git status easily |  
| **Stash before pull** | Optional | Safer if you edit on multiple PCs |  
  
> 💾 **Credential hint:** Git for Windows includes a Credential Manager, so once you log in once, it remembers your credentials.  
  

## 7) Daily Workflow (Windows)  
**Morning:**  
- Open Obsidian → it auto-pulls from GitHub.  
  
**During the day:**  
- Notes are auto-committed & pushed every 10–15 minutes.  
  
**End of the day:**  
- Manually run `Git: Push` (Ctrl + P → type `git push`) to ensure remote sync.  
  
**On another PC:**  
- Clone the repo:  
```powershell  
cd "C:\Users\YourName\Documents"  
git clone <REMOTE_URL> MyVault  
```  
- Open `MyVault` in Obsidian → enable the Git plugin with same settings.  
  
---

## 8) Solving Common Issues  
**Push rejected (non-fast-forward):**  
```powershell  
git pull --rebase  
git push  
```  
  
**Obsidian Git says “not a git repo”:**  
```powershell  
git rev-parse --is-inside-work-tree  
```  
Make sure this returns `true` and that `.git` exists in your vault folder.  
  
**Auth prompts repeatedly:**  
- Ensure Git Credential Manager is enabled.  
- Try:  
```powershell  
git config --global credential.helper manager  
```  
  
**Wrong username/email:**  
```powershell  
git config --global user.name "Your Name"  
git config --global user.email "you@example.com"  
```

## 9) Optional: Git LFS (Large Files)  
If your vault has large PDFs or images:  
```powershell  
git lfs install  
git lfs track "*.pdf"  
git lfs track "*.png"  
git add .gitattributes  
git commit -m "Enable Git LFS"

## 10) Quick Summary Checklist ✅
- [ ] Installed **Git for Windows**  
- [ ] Verified Git version  
- [ ] Initialized repo in vault  
- [ ] Created `.gitignore`  
- [ ] Connected remote  
- [ ] First commit & push  
- [ ] I

