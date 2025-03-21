# resources and docs for setting up my dev environment

### SVELTE

https://svelte.dev/tutorial/svelte/welcome-to-svelte

<script>
	import Nested from 
	let var='Variable';
	let src="./image.jpg';
</script>
<p>Hello {var.toLowerCase()}</p>
<img {src} />
<style> p { font-size: 2em; } </style>


### GIT

git --version

# generate SSH key
# by default, the key will be saved in ~/.ssh/id_rsa.

ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

# Add SSH Key to GitHub

Go to GitHub SSH settings.
Copy the contents of your public key (~/.ssh/id_rsa.pub).
Add the key to GitHub by clicking New SSH key and pasting the contents.

# Test SSH Connection

ssh -T git@github.com

# Configure VSCode to Use Your Organization’s GitHub Account

Open the Command Palette (Ctrl + Shift + P or Cmd + Shift + P on macOS).
Type GitHub: Sign in and select it.
Follow the prompts to sign in to your GitHub account (the organization’s account should be listed).