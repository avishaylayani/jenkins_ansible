pipeline {
    agent any
    
    stages {      
        stage("Execute Ansible") {
            steps {
                ansiblePlaybook  disableHostKeyChecking: true,
                                 installation: 'Ansible',
                                 inventory: 'hosts.ini',
                                 playbook: 'facts_gathering.yml'
            }    
        }    
    }
}