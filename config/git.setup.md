# Setting Up GitHub SSH Access

## 1. Check for Existing SSH Keys

```bash
ls -al ~/.ssh
```

Look for files named `id_ed25519` / `id_ed25519.pub` or `id_rsa` / `id_rsa.pub`. If they exist, you can skip to step 3.

## 2. Generate a New SSH Key

```bash
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519_personal -C "your_email@example.com"
```

When prompted:
- Enter a passphrase (recommended) or press **Enter** for none.

> If your system doesn't support Ed25519, fall back to RSA:
> ```bash
> ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
> ```

## 3. Start the SSH Agent and Add Your Key

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519_personal
```

### macOS: Persist the Key Across Reboots

Add the following to `~/.ssh/config` (create the file if it doesn't exist):

```text
Host github.com-personal
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_rsa_personal
   IdentitiesOnly yes

Host github.com-work
   HostName github.com
   User git
   IdentityFile ~/.ssh/id_ed25519_work
```

Then load the key into the keychain (optional):

```bash
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

## 4. Copy the Public Key

```bash
pbcopy < ~/.ssh/id_ed25519_personal.pub   # macOS
```

On Linux, use one of:

```bash
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
cat ~/.ssh/id_ed25519.pub        # then copy manually
```

## 5. Add the Key to GitHub

1. Go to **GitHub → Settings → SSH and GPG keys** ([direct link](https://github.com/settings/keys)).
2. Click **New SSH key**.
3. Give it a descriptive **Title** (e.g. `MacBook Pro 2025`).
4. Set **Key type** to **Authentication Key**.
5. Paste the public key into the **Key** field.
6. Click **Add SSH key**.

## 6. Verify the Connection

```bash
ssh -T git@github.com-personal
```

Expected output:

```text
Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.
```

## 7. Configure Git to Use SSH

For new clones, use the SSH URL:

```bash
git clone git@github.com-personal:owner/repo.git
```

To switch an existing repo from HTTPS to SSH:

```bash
git remote set-url origin git@github.com-personal:owner/repo.git
```

Verify:

```bash
git remote -v
```

## Troubleshooting

| Symptom | Fix |
|---|---|
| `Permission denied (publickey)` | Make sure the key is added to the agent (`ssh-add -l`) and to GitHub. |
| Agent not running | Run `eval "$(ssh-agent -s)"` again. |
| Wrong key offered | Specify the key explicitly in `~/.ssh/config`. |
| Passphrase prompt every time (macOS) | Add `UseKeychain yes` to `~/.ssh/config` as shown above. |

# Git Config setup

Can setup differnt user name and email by workspace.

```
# in ~/.gitconfig

[includeIf "gitdir:~/code/"]
    path = ~/.gitconfig-work

[includeIf "gitdir:~/workspace/"]
    path = ~/.gitconfig-jz

# in .gitconfig-work
[user]
	name = <name>
	email = <work email>

# in .gitconfig-personal
[user]
	name = <name>
	email = <personal@email>
```

Then in individual repo, you can override for the repo only with git config commands.

```
git config user.name "<github user id>"
git config user.email <email>
```