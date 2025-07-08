pipeline {
    agent any
    withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
    sh 'docker push devopstechlab/tomcat:v3'
    sh 'docker tag devopstechlab/tomcat:v3 devopstechlab/tomcat:latest'
    sh 'docker push devopstechlab/tomcat:latest'
}

    stages {
        stage('Download-Code-GIT') {
            steps {
                echo "Download code from git"
                git branch: 'main', url: 'https://github.com/devopstechlab/maven-jenkins7.git'
            }
        }
        stage('Build') {
            steps {
        sh '''docker build -t devopstechlab/tomcat:v${BUILD_NUMBER} .
            docker tag devopstechlab/tomcat:v${BUILD_NUMBER} devopstechlab/tomcat:latest 
            docker push devopstechlab/tomcat:v${BUILD_NUMBER}
            docker push devopstechlab/tomcat:latest '''
            }
        }
    }
}
