
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
        stage('Build') {
             steps{
                script{
                    sh " ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml"
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
         stage('push docker hub') {
             steps{
                script{
                    sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml "
                }
            }
        }
        }    
        }
