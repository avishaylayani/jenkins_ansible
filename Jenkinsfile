pipeline {
    agent { label 'workers' }
    parameters { // Setting parameters for nginx config, and the title that will be displayed in the HTML
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
        stage("Running Installations playbook - Installs nginx") {
            steps{
                script {
                    ansiblePlaybook(
                        disableHostKeyChecking: true,
                        installation: 'Ansible',
                        inventory: 'playbooks/hosts.ini',
                        playbook: 'playbooks/installations.yml',
                        credentialsId: 'ansible-jenkins',
                    )
                }
            }
        }
        stage ('Copying nginx.conf and html.index jinja templates to the host'){
            steps{
                script {
                    def extraVarsString = "port=${params.port} index_file=${params.index_file} server=${params.server} title=${params.title}"
                    ansiblePlaybook(
                        disableHostKeyChecking: true,
                        installation: 'Ansible',
                        inventory: 'playbooks/hosts.ini',
                        playbook: 'playbooks/copy_templates.yml',
                        credentialsId: 'ansible-jenkins',
                        extras: "--extra-vars '${extraVarsString}'"
                    )
                }
            }
        }    
    }      
}
