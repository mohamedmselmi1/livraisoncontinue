
 pipeline {
  agent any
    stages {
        stage('Pull') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                        userRemoteConfigs: [[
                            credentialsId: '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',
                            url: 'https://github.com/mohamedmselmi1/livraisoncontinue.git']]])
                }
            }
        }
        stage('docker') {
             steps{
                script{
             sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml "
                }
            }
        }
        }    
        }
