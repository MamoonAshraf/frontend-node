pipeline{
    agent { dockerfile true }
    stages{
        stage ('SCM Gitcheckout'){
           steps{
               git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/MamoonAshraf/frontend-node' 
           } 
        }
        stage ('Build Docker Image'){
            steps {
                sh 'docker build -t mamoon123/frontend-app:v1.1 .'
            }
        }
        
        stage ('Docker Push'){
            steps {
                withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
        sh "docker login -u mamoon123 -p ${dockerHubPwd}"
		sh 'docker push mamoon123/frontend-app:V1.0'
     } 
            }
        }
    }
    
}