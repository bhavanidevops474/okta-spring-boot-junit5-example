pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                git branch: 'main', url: 'https://github.com/bhavanidevops474/okta-spring-boot-junit5-example.git'
            }
            }
        }
        stage('Clean') {
            steps {
                script {
                "mvn test -Dtest=BirthdayInfoControllerIT" 
            }
            }
        }
    }
}
