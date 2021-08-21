node {

    stage("Git Clone"){

        git credentialsId: 'git-cred', url: 'https://github.com/MamoonAshraf/frontend-node.git'
    }

     stage('Build') {

       sh 'npm install'

    }

    stage("Docker build"){
        sh 'docker version'
        sh 'docker build -t mamoon123/frontend-app:v1.1 .'
        sh 'docker image list'
      
    }

    withCredentials([string(credentialsId: 'DOCKER_HUB_PASSWORD', variable: 'PASSWORD')]) {
        sh 'docker login -u mamoon123 -p $PASSWORD'
    }

    stage("Push Image to Docker Hub"){
        sh 'docker push  mamoon123/frontend-app:v1.1'
    }

    stage("SSH Into Minikub Server") {
        def remote = [:]
        remote.name = ''
        remote.host = ''
        remote.user = ''
        remote.password = ''
        remote.allowAnyHosts = true

        stage('Put k8s-fronendt-deployment.yml onto k8smaster') {
            // pending
        }

        stage('Deploy frontend') {
         // for now manually changing image version in deployment.yaml file to deploy
        }
    }

}
