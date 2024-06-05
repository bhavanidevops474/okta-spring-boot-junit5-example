pipeline {
    agent any
    tools {
        maven 'maven-3.6.3'
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                git branch: 'main', url: 'https://github.com/bhavanidevops474/okta-spring-boot-junit5-example.git'
            }
            }
        }
        stage('Build'){
            steps {
                script {
                    "mvn clean package"
                }
            }
        }
        stage('Test') {
            steps {
                script {
                "mvn test -Dtest=BirthdayInfoControllerIT" 
            }
            }
        }
    }
}
         
