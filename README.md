# Second Branch : Golden SSH Key for Passwordless connection
### Takes Parameters:
- Hosts from the hosts file (File exists on every branch with a playbook)
- Golden ssh key for future remote connection
- Ansible Credentials - Used for the ansible playbook
### steps:
- Creating .ssh file under root's home user, in case it doesn't exist
- Creating authorized_keys file, if doesn't exist
- Adding the golden_ssh_key.pub's text into authorized_keys file
- Copying the private key locally to the worker for testing(To test the ssh passwordless connection
