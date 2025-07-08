pipeline {
    agent any

stages {
        stage('Download-Code-GIT') {
            steps {
                echo "Download code from git"
                git branch: 'main', url: 'https://github.com/nil7405/maven-jenkins7.git'
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
