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
                sh '''


                '''
                
            }    
        }      
    }
}
