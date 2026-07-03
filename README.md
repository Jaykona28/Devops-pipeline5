In my recent project, I built a fully automated CI/CD pipeline using GitHub Actions and Ansible.
For the CI phase, GitHub Actions builds a lightweight Alpine-based Docker image and pushes it to a registry.
For the CD phase, I used Ansible to pull the image and deploy it. 
However, because I was designing this with strict resource constraints in mind—similar to constrained production environments—I didn't want to run a heavy, 
persistent CI server like Jenkins. Instead, I used ephemeral GitHub Actions runners. The runner installs Ansible on the fly, 
executes the playbook to deploy the container with strict memory limits (--memory=256m), and then the runner terminates.
In a production environment, I would simply update the Ansible hosts inventory to point to our actual target servers—like 
AWS EC2 instances—using SSH keys stored in GitHub Secrets, rather than deploying to localhost. This approach keeps the pipeline lightweight, secure, and 
completely automated."
