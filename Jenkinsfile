pipeline {
    agent { label 'workers' }
    parameters {
        string(name: 'port', 
            defaultValue: '4000',
            description: 'The port that Nginx will be accessible on'
        )
        string(name: 'index_file',
            defaultValue: "index.html",
            description: 'Simple HTML file to be presented via Nginx'
        )
        string(name: 'server',
        defaultValue: "localhost",
        description: 'The server that contains the HTML file, in this case it will be localhost'
        )
        string(name: 'title',
        defaultValue: "BIG TITLE",
        description: 'The only line in the HTML file, can be modified here'
        )        
    }
    stages {      
        stage("Running Installations playbook") { //Installs Nginx
            steps {
                script {
                    ansiblePlaybook(
                        disableHostKeyChecking: true,
                        installation: 'Ansible',
                        inventory: 'hosts.ini',
                        playbook: 'playbooks/installations.yml',
                        credentialsId: 'ansible-jenkins',
                    )
                }
            }
            steps {
                script {
                    def extraVarsString = "port=${port} index_file=${index_file} server=${server} title=${title}"
                    ansiblePlaybook(
                        disableHostKeyChecking: true,
                        installation: 'Ansible',
                        inventory: 'hosts.ini',
                        playbook: 'playbooks/copy_templates.yml',
                        credentialsId: 'ansible-jenkins',
                        extras: "--extra-vars '${extraVarsString}'"
                    )
                }
            }
        }    
    }      
}
