pipeline {
    agent { label 'workers' }
    stages {      
        stage("Testing Ansible") {
            steps {
                withCredentials([usernamePassword(credentialsId: 'admin_credentials_id', 
                usernameVariable: 'ADMIN_USERNAME',
                passwordVariable: 'ADMIN_PASSWORD')]) {
                    ansiblePlaybook  disableHostKeyChecking: true,
                        installation: 'Ansible',
                        inventory: 'hosts.ini',
                        playbook: 'facts_gathering.yml',
                        credentialsId: 'ansible-jenkins'
                }
            }    
        }      
    }
}
