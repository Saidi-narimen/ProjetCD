pipeline {
    agent any
    stages {
        stage ("Pull") {
            steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/Saidi-narimen/ProjetCD.git']]])
                }
            }
        }
     stage('python test'){
            steps{
                script{
                    sh "python3 --version"
                }
            }
        }
   
     stage('Build'){
            steps{
                script{
                    sh "ANSIBLE_DEBUG=1 ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }
		
       
    }
     stage('docker'){
            steps{
                script{
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml"
                }
            }
        }
}
}
