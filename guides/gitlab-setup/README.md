# Connecting Claude Code to Red Hat Internal GitLab

**Audience**: Red Hat associates who have Claude Code installed and want it to create MRs, review code, and comment on gitlab.cee.redhat.com

**Time needed**: 10 minutes

**What you'll walk away with**: Claude Code that can list, create, review, and comment on Merge Requests on Red Hat's internal GitLab — all from natural language

---

## Before You Start
- Claude Code CLI installed and working (`claude` command works in your terminal)
- VPN connected (gitlab.cee.redhat.com is internal)
- A Red Hat Kerberos account (same one you use for everything)

---

## Step-by-Step Setup

### Step 1: Install the GitLab CLI (glab)

<details>
<summary><strong>Windows</strong></summary>

Open PowerShell or Command Prompt and run:

```powershell
winget install GLab.GLab
```

After install, close and reopen your terminal so it picks up the new PATH.

> **Stuck?** If `glab` isn't found after install, check `C:\Users\YOUR_USERNAME\AppData\Local\Programs\glab\` — the exe might be there but not in your PATH. You can run it with the full path instead.

</details>

<details>
<summary><strong>macOS</strong></summary>

Open Terminal and run:

```bash
brew install glab
```

If you don't have Homebrew, install it first: https://brew.sh

</details>

<details>
<summary><strong>Linux (Fedora / RHEL)</strong></summary>

```bash
sudo dnf install glab
```

For other distros, download the latest release from https://gitlab.com/gitlab-org/cli/-/releases and add it to your PATH.

</details>

Verify it installed (all platforms):

```bash
glab --version
```

You should see something like `glab version 1.x.x`.

---

### Step 2: Create a Personal Access Token (PAT)

This step is the same on all platforms — it's done in your browser.

1. Open your browser and go to:
   ```
   https://gitlab.cee.redhat.com/-/user_settings/personal_access_tokens
   ```

2. Fill in:
   - **Token name**: `claude-code`
   - **Expiration date**: pick something reasonable (90 days, or blank for no expiry)
   - **Scopes**: check these boxes:
     - `api` (full access)
     - `read_user` (read your profile)

3. Click **Create personal access token**

4. **Copy the token immediately** — you won't see it again

> **Important**: This token is like a password. Don't share it, don't commit it to git, don't paste it in Slack.

---

### Step 3: Authenticate glab with the token

<details>
<summary><strong>Windows (PowerShell)</strong></summary>

```powershell
"glpat-YOUR_TOKEN_HERE" | glab auth login --hostname gitlab.cee.redhat.com --stdin
```

If using Git Bash or WSL:
```bash
echo "glpat-YOUR_TOKEN_HERE" | glab auth login --hostname gitlab.cee.redhat.com --stdin
```

</details>

<details>
<summary><strong>macOS / Linux</strong></summary>

```bash
echo "glpat-YOUR_TOKEN_HERE" | glab auth login --hostname gitlab.cee.redhat.com --stdin
```

</details>

Replace `glpat-YOUR_TOKEN_HERE` with the token you copied in Step 2.

Verify it worked (all platforms):

```bash
glab auth status --hostname gitlab.cee.redhat.com
```

You should see:
```
gitlab.cee.redhat.com
  ✓ Logged in as YOUR_USERNAME
```

---

### Step 4: Tell Claude Code to allow glab commands

Open Claude Code and say:

```
allow glab commands
```

Claude will add `Bash(glab:*)` to your permissions so it won't ask for approval every time it runs a glab command.

Alternatively, you can add it manually:

<details>
<summary><strong>Windows</strong></summary>

Edit `%USERPROFILE%\.claude\settings.local.json` and add to the `permissions.allow` array:
```json
"Bash(glab:*)"
```

</details>

<details>
<summary><strong>macOS / Linux</strong></summary>

Edit `~/.claude/settings.local.json` and add to the `permissions.allow` array:
```json
"Bash(glab:*)"
```

</details>

---

### Step 5: Test it

Open Claude Code in a directory with a git repo that has `gitlab.cee.redhat.com` as its remote. Then try:

```
list my open merge requests on gitlab
```

Claude should run `glab mr list` and show you your MRs.

---

## What You Can Now Ask Claude

| What you say | What Claude does |
|---|---|
| "list my open merge requests" | `glab mr list` |
| "create a merge request for my changes" | `glab mr create` with auto-generated title and description |
| "show me MR 5" | `glab mr view 5` — shows diff, comments, status |
| "review the diff on MR 12" | `glab mr diff 12` — Claude reads the code and gives feedback |
| "comment on MR 3 that the tests look good" | `glab mr note 3 -m "..."` |
| "approve MR 7" | `glab mr approve 7` |
| "what pipelines are running" | `glab ci list` |
| "check the CI status on MR 2" | `glab ci view` |

---

## Troubleshooting

| Problem | Platform | Fix |
|---|---|---|
| `glab: command not found` | Windows | Close and reopen terminal, or use full path: `C:\Users\YOU\AppData\Local\Programs\glab\glab.exe` |
| `glab: command not found` | macOS | Run `brew link glab` or check `brew info glab` for the install path |
| `glab: command not found` | Linux | Make sure the binary is in your PATH: `which glab` or `echo $PATH` |
| `401 Unauthorized` | All | Your PAT expired or doesn't have the right scopes. Create a new one (Step 2) |
| `Could not resolve host: gitlab.cee.redhat.com` | All | You're not on VPN. Connect and try again |
| Claude keeps asking permission for glab | All | Say `allow glab commands` or add `Bash(glab:*)` to settings |
| `SSL certificate problem` | macOS/Linux | Your machine may not have the Red Hat internal CA. Try: `export GIT_SSL_NO_VERIFY=1` as a temporary workaround, or install the RH CA bundle |
| `remote: The project you were looking for could not be found` | All | Make sure you're in a directory with a git remote pointing to gitlab.cee.redhat.com, or specify the repo: `glab mr list --repo YOUR_GROUP/YOUR_REPO` |
| PowerShell pipe doesn't work for auth | Windows | Use Git Bash instead, or try: `glab auth login --hostname gitlab.cee.redhat.com` (interactive mode) |

---

## What's Next

You just connected Claude Code to Red Hat's internal GitLab. You can now:
- Create MRs from natural language
- Review code without opening a browser
- Comment and approve from your terminal

**Next level**: Ask Claude to "review my changes and create a merge request with a good description" — it'll read your diff, write the MR description, and create it in one shot.
