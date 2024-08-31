pipeline {
    agent { label 'workers' }

    environment {
                withCredentials([usernamePassword(credentialsId: 'admin_credentials_id', 
                usernameVariable: 'ADMIN_USERNAME',
                passwordVariable: 'ADMIN_PASSWORD')]){
                    username = "${params.ADMIN_USERNAME}",
                    password = "${params.ADMIN_PASSWORD}"
                }
    }
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
