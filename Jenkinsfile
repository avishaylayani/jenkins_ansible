pipeline {
    agent { label 'workers' }
    stages {      
        stage("Testing Ansible") {
            steps {
                withCredentials([usernamePassword(credentialsId: 'admin_credentials_id', 
                usernameVariable: 'ADMIN_USERNAME',
                passwordVariable: 'ADMIN_PASSWORD')]) {
                    sh ' echo "${ADMIN_USERNAME}" '
                }
            }    
        }      
    }
}
