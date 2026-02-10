## Codeberg Mirror Setup

This repository mirrors all commits to Codeberg via GitHub Actions.

### Steps

1. Create a repository on Codeberg
2. Generate an SSH key **on your local machine**:
    ```bash
    ssh-keygen -t ed25519 -C "github-actions-mirror"
    ```
3. Add the public key to Codeberg:
  - Repository → Settings → Deploy Keys
  - Allow write access

4. Add the private key to GitHub:
  - GitHub repo → Settings → Secrets → Actions
  - Name: CODEBERG_SSH_KEY
  - Value: (private key content)

5. Edit .github/workflows/codeberg.yml:
  - Move `codeberg.yml` to `workflows/codeberg.yml`
  - Replace <CODEBERG_USER>/<REPO>
  - Replace other configuration necessary for your repository

### Caveats

That means **one of these is true**:

### ❌ Common mistakes

1. **Deploy key added at user level**
   - ❌ Codeberg SSH keys (profile)
   - ✅ Must be **Deploy Key on the target repository**

2. **Write access not enabled**
   - Must check **“Allow write access”**

3. **Wrong repository**
   - Key added to a different repo than your aims

4. **Wrong private key**
   - GitHub secret does not match the public key uploaded

Your SSH setup itself is **correct**.  
Your `ssh-keyscan` warnings are **harmless**.