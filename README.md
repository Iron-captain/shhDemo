# SSH Connection Demo

This project demonstrates how to set up SSH keys and connect to GitHub using SSH, as well as how to create and connect a repository using the GitHub CLI (`gh`).

## Prerequisites
- [Git](https://git-scm.com/downloads) installed
- [GitHub CLI (`gh`)](https://cli.github.com/) installed
- A GitHub account

## 1. Generate SSH Key and Add to SSH Agent

```bash
# Generate a new SSH key (replace email with your GitHub email)
ssh-keygen -t ed25519 -C "hraj00036@gmail.com"

# Start the ssh-agent in the background
eval "$(ssh-agent -s)"

# Add your SSH private key to the ssh-agent
ssh-add ~/.ssh/id_ed25519
```

## 2. Add SSH Key to GitHub
- Copy the contents of your public key to your clipboard:
  ```bash
  cat ~/.ssh/id_ed25519.pub
  ```
- Go to [GitHub SSH settings](https://github.com/settings/keys) and add a new SSH key.

## 3. Test SSH Connection
```bash
ssh -T git@github.com
```
You should see a success message if everything is set up correctly.

## 4. Authenticate GitHub CLI
```bash
gh --version  # Check if gh is installed
gh auth login # Follow the prompts to authenticate
```

## 5. Create a New Repository and Add Remote
```bash
# Create a new repository (replace <repo-name> and choose --public or --private)
gh repo create <repo-name> --public --confirm --source=. --remote=origin

# If you need to add the remote manually:
git remote add origin git@github.com:<your-username>/<repo-name>.git
```

## Resources
- [GitHub Docs: Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- [GitHub CLI Documentation](https://cli.github.com/manual/)

