# Ansible Jenkins Pipeline

Creates Jenkins multi-branch pipeline that will take remote host ip address, type of remote host(server or desktop or laptop), username, password, sshkey, dedicated list of packages and dedicated config files. All the details will be used to setup the remote host with all the provided data to pipeline via ansible playbooks/roles

### Tasks

- Create jenkins multi-branch pipeline
    - Should take parameters of:
        - Host ip - where to connect
        - Username - user that suppose to be create, if it does not exists
        - Password - password for that user, should be either encrypted with ansible or saved in jenkins
        - Golden ssh key for future remote connection
        - List of packages - software to install, may be predefined in playbook
        - Dedicated config files - config for installed software, you may use templates
        
    - Jenkins should use ansible plugin
    - Ansible playbooks/roles can be used from previous modul or written from scratch


### Notes

- Ansible plugin for jenkins requires additional configuration, please RTFM


