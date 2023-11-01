pipeline {
    agent any
    stages {
        stage('vcs') {
            steps {
checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Sshakshi16/nodejsapplicationtest.git']])        
sh "ls"
sh '''
   cd "./login-registration-server-node" && ls && docker build -t sakshisawalikar16/terraform-repo:latest .
  
   '''
            }
        }
  stage('docker push') {
            steps {
 withCredentials([usernamePassword(credentialsId: 'batch2', passwordVariable: 'demobatchpass', usernameVariable: 'demobatchuser')]) {
 sh "docker login -u ${env.demobatchuser} -p ${env.demobatchpass}"
 sh "docker push sakshisawalikar16/terraform-repo:latest"

     }
            }
        }
    }
}
 
sh "docker login -u ${env.demobatchuser} -p ${env.demobatchpass}" : used to login in to the docker hub using the variables that we have created.
sh "docker push sakshisawalikar16/terraform-repo:latest" : used to push the code into the repo in the docker hub.
