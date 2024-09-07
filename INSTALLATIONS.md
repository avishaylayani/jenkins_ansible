# Installations

### Step 1
- clone git https://github.com/lavishay-technion/jenkins_ansible.git
- Go to docker directory and run docker compose up -d
    * This is downloading and running the Jenkins CI/CD
### Step 2
- Go into Jenkins localhost:80
- Run the Multi-Branch pipeline "Jenkins Ansible"
- Check the results:
    - admin user on the target hosts creation
    - Connecting via passwordless key SSH with the golden_ssh_key
    - Opening localhost:100 and localhost:200 to see the html presented via NGINX
