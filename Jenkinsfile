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
        sh '''docker build -t nil7405/tomcat:v${BUILD_NUMBER} .
            docker tag nil7405/tomcat:v${BUILD_NUMBER} nil7405/tomcat:latest 
            docker push nil7405/tomcat:v${BUILD_NUMBER}
            docker push nil7405/tomcat:latest '''
            }
        }
    }
}
