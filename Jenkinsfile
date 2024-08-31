pipeline {
    agent { label 'workers' }
    stages {      
        stage("Testing Ansible") {
            steps {
                ansiblePlaybook(
                    disableHostKeyChecking: true,
                    installation: 'Ansible',
                    inventory: 'hosts.ini',
                    playbook: 'deploying_ssh_key.yml',
                    credentialsId: 'ansible-jenkins'
                    )
                }
            }    
        }      
    }
}
