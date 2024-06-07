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
                sh 'mvn -B -DskipTests clean package'
                
            }
        }
        stage('Test') {
            steps {
                
                sh 'mvn clean test' 
            
            }
        }

         post {
             stage {
                 steps {
        always {
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
            junit 'build/reports/**/*.xml'
        }
    }
             }
         }

    }
}
