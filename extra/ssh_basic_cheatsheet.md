# SSH Basics Cheat Sheet (for GitHub Access)

SSH (Secure Shell) allows you to securely connect to remote services like GitHub without typing your username and password every time. Here's how to set it up step-by-step:

---
## 1. Check if SSH is installed

```bash
ssh -V
```
This command displays the SSH version. If SSH is installed, you'll see output like "OpenSSH_8.1p1".
## 2. Install SSH (if not already installed)

- SSH usually comes pre-installed with Git Bash. 
- Download Git for Windows from https://git-scm.com/download/win
## 3. Check for Existing SSH Keys
Check if you already have an SSH key 

windows: `C:\Users\<YourName>\.ssh`

git bash terminal:
```bash
ls -al ~/.ssh
# Look for files like id_rsa (private) and id_rsa.pub (public).
-rw------- 1 username username 1675 Dec 16 10:00 id_rsa
-rw-r--r-- 1 username username 400 Dec 16 10:00 id_rsa.pub
```
To view your public key:
`cat ~/.ssh/id_rsa.pub`

## 4. Generating SSH Keys
Generate a new SSH key pair (RSA recommended):

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
``` 
Follow the prompts. Press Enter to accept default file location (~/.ssh/id_rsa)

Set a passphrase (optional but recommended)

## 5. Start SSH Agent

```bash
eval "$(ssh-agent -s)"
```

## 6. Add SSH Key to Agent


```bash
ssh-add ~/.ssh/id_rsa
```


## 7. Copy SSH Public Key

```bash
cat ~/.ssh/id_rsa.pub
```
Now copy all from the first string 'ssh-rsa' until the 'email@email.com'
```
ssh-rsa AAAAB3Nz...long strings without triple dots ... l9oGeidlGSFaw== youremail@gmail.com
```
## 8. Add SSH Key to GitHub/GitLab

1. Go to your account settings on GitHub
2. Find "SSH Keys" or "SSH and GPG keys" section
3. Click "New SSH key" or "Add SSH key"
4. Paste your public key and save

## 8. Test SSH Connection

For GitHub:

```bash
ssh -T git@github.com
# When successfull
# Hi yourname! You've successfully authenticated, but GitHub does not provide shell access.
```