# 🔐 Complete Guide: Setting Up GitHub Secrets & Tokens for Spectral Profile

## 🌙 Step-by-Step Secret Configuration

### 1. 🚀 GITHUB_TOKEN (Usually Auto-Available)

**Good News**: `GITHUB_TOKEN` is automatically provided by GitHub Actions in most cases!

#### ✅ **No Action Needed (Recommended)**
- GitHub automatically provides `${{ secrets.GITHUB_TOKEN }}` 
- Has standard permissions for your repository
- Works for most profile features

#### 🔧 **If You Need Custom Permissions** (Advanced)
Sometimes you might need a Personal Access Token with specific permissions:

1. Go to **GitHub.com** → Click your **profile picture** (top right)
2. Navigate to **Settings** → **Developer settings** (bottom left)
3. Click **Personal access tokens** → **Tokens (classic)**
4. Click **Generate new token** → **Generate new token (classic)**
5. Configure your token:
   ```
   Name: GitHub Profile Token
   Expiration: 90 days (or custom)
   
   Select scopes:
   ☑️ repo (Full repository access)
   ☑️ workflow (Update GitHub Actions workflows)
   ☑️ read:user (Read user profile data)
   ☑️ user:email (Access user email addresses)
   ```
6. Click **Generate token**
7. **⚠️ IMPORTANT**: Copy the token immediately (you won't see it again!)

---

### 2. 🔮 METRICS_TOKEN (Required for Advanced Spectral Metrics)

This token is needed for the advanced metrics workflow to access detailed GitHub data.

#### 📋 **Step-by-Step Creation:**

1. **Go to GitHub Settings**:
   - Click your profile picture → **Settings**
   - Scroll down to **Developer settings**
   - Click **Personal access tokens** → **Tokens (classic)**

2. **Generate New Token**:
   - Click **Generate new token** → **Generate new token (classic)**
   
3. **Configure Token Settings**:
   ```
   Token Name: Spectral Metrics Token
   Expiration: 90 days (recommended) or No expiration
   
   Required Scopes for Metrics:
   ☑️ repo (Full repository access)
   ☑️ read:user (Read all user profile data)
   ☑️ read:org (Read org data - if you're in organizations)
   ☑️ user:email (Access user email addresses)
   
   Optional (for enhanced metrics):
   ☑️ read:project (Read project data)
   ☑️ public_repo (Access public repositories)
   ```

4. **Generate & Copy**:
   - Click **Generate token**
   - **📋 Copy the token immediately** - you won't see it again!
   - It looks like: `ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

---

### 3. 🕸️ Adding Secrets to Your Repository

#### **Method 1: Via GitHub Web Interface** (Recommended)

1. **Navigate to Your Profile Repository**:
   - Go to `github.com/Ktejas99/Ktejas99` (your profile repo)

2. **Access Repository Settings**:
   - Click **Settings** tab (top navigation bar)
   - If you don't see Settings, make sure you're the owner of the repository

3. **Navigate to Secrets**:
   - In the left sidebar, expand **Secrets and variables**
   - Click **Actions**

4. **Add Your Secrets**:
   
   **For METRICS_TOKEN**:
   - Click **New repository secret**
   - **Name**: `METRICS_TOKEN`
   - **Secret**: Paste your personal access token
   - Click **Add secret**

   **For Custom GITHUB_TOKEN** (if needed):
   - Click **New repository secret**  
   - **Name**: `GITHUB_TOKEN`
   - **Secret**: Paste your personal access token
   - Click **Add secret**

#### **Method 2: Via GitHub CLI** (Advanced)

```bash
# Install GitHub CLI first: https://cli.github.com/

# Login to GitHub
gh auth login

# Navigate to your profile repository
cd /path/to/Ktejas99

# Add METRICS_TOKEN
gh secret set METRICS_TOKEN

# Add custom GITHUB_TOKEN (if needed)
gh secret set GITHUB_TOKEN
```

---

### 4. 🌟 Verification & Troubleshooting

#### ✅ **How to Verify Secrets Are Added**:

1. Go to your repository **Settings** → **Secrets and variables** → **Actions**
2. You should see:
   ```
   Repository secrets:
   • METRICS_TOKEN ✓
   • GITHUB_TOKEN ✓ (if you added a custom one)
   ```

#### 🔧 **Common Issues & Solutions**:

**Issue**: "GITHUB_TOKEN doesn't have permission"
- **Solution**: The auto-provided token usually works. If not, create a custom one with `repo` and `workflow` scopes.

**Issue**: "METRICS_TOKEN not found"
- **Solution**: Make sure you named it exactly `METRICS_TOKEN` (case-sensitive)

**Issue**: "Token has insufficient permissions"
- **Solution**: Recreate the token with all required scopes checked

**Issue**: "Workflows not running"
- **Solution**: 
  1. Check that GitHub Actions are enabled in Settings → Actions → General
  2. Ensure repository is public or you have GitHub Pro/Team
  3. Verify secrets are correctly named and saved

#### 🚨 **Security Best Practices**:

- ✅ **Set token expiration** (90 days recommended)
- ✅ **Use minimal required scopes**
- ✅ **Regularly rotate tokens**
- ✅ **Never commit tokens to code**
- ✅ **Monitor token usage in Settings → Developer settings**

---

### 5. 📊 Testing Your Setup

After adding secrets, test the workflows:

1. **Manual Trigger**:
   - Go to **Actions** tab in your repository
   - Click on any workflow
   - Click **Run workflow** → **Run workflow**

2. **Check Workflow Logs**:
   - Click on the running workflow
   - Expand steps to see if tokens are working
   - Look for authentication errors

3. **Expected Results**:
   - Spectral activity updates in README
   - Snake animation generated
   - Metrics SVG created
   - Profile views tracking working

---

### 6. 🎯 Final Checklist

Before your spectral profile goes live:

- [ ] Profile repository created (`username/username`)
- [ ] README.md added to repository root
- [ ] All 4 workflow files in `.github/workflows/`
- [ ] `METRICS_TOKEN` secret added with correct permissions
- [ ] Repository is public
- [ ] GitHub Actions enabled
- [ ] Personal links updated in README
- [ ] First workflow run completed successfully

---

### 🌙 You're All Set!

Once these secrets are configured, your spectral GitHub profile will automatically:
- 👻 Update ghost activities every 6 hours
- 🐍 Generate haunted snake animations every 12 hours  
- 📊 Create advanced metrics daily
- 👁️ Track spectral visitors continuously

Your otherworldly developer presence will be **fully automated** and **absolutely unique**! ✨🔮👻
