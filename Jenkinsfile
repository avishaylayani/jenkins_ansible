pipeline {
    agent { label 'workers' }
    stages {      
        stage("Testing Ansible") {
            steps {
                withCredentials([string(credentialsId: 'golden_ssh_key.pub', variable: 'GOLD_KEY')]) {
                    script {
                        def extraVarsString = "new_user=${ADMIN_USERNAME} new_password=${ADMIN_PASSWORD}"
                        ansiblePlaybook(
                            disableHostKeyChecking: true,
                            installation: 'Ansible',
                            inventory: 'hosts.ini',
                            playbook: 'facts_gathering.yml',
                            credentialsId: 'ansible-jenkins',
                            extras: "--extra-vars '${extraVarsString}'"
                        )
                    }
                }
            
            }
        }    
    }      
}
