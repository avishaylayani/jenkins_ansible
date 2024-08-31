pipeline {
    agent { label 'workers' }
    
    stages {      
        stage("Execute Ansible") {
            steps {
                sh '''
                    ansible --version
                    ansible-playbook --version
                    ansible-galaxy --version

                '''
                
            }    
        }  
        stage("Testing Ansible") {
            steps {
                ansiblePlaybook credentialsid: 'Ansible_Jenkins', disableHostKeyChecking: true, installation: 'Ansible',
                ansiblePlaybook  disableHostKeyChecking: true,
                    installation: 'Ansible',
                    inventory: 'hosts.ini',
                    playbook: 'facts_gathering.yml'
            }    
        }      
    }
}
