pipeline {
    agent { label 'workers' }
    stages {      
        stage("Testing Ansible") {
            steps {
                withCredentials([usernamePassword(credentialsId: 'admin_credentials_id', 
                usernameVariable: 'ADMIN_USERNAME',
                passwordVariable: 'ADMIN_PASSWORD')]) {
                    script {
                        def extraVarsString = "new_user=${ADMIN_USERNAME} new_password=${ADMIN_PASSWORD}"
                        ansiblePlaybook(
                            disableHostKeyChecking: true,
                            installation: 'Ansible',
                            inventory: 'hosts.ini',
                            playbook: 'user_creation.yml',
                            credentialsId: 'ansible-jenkins',
                            extras: "--extra-vars '${extraVarsString}'"
                        )
                    }
                }
            }    
        }      
    }
}
