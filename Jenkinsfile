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
       stage('Package') {
            steps {
                sh 'mvn clean package'  
                //archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
                junit '**/target/surefire-reports/*.xml'
            }
        }
        stage("SonarQube analysis") {
            steps {
              withSonarQubeEnv('My SonarQube Server') {
                sh 'mvn clean package sonar:sonar'
              }
            }
          }
          stage("Quality Gate") {
            steps {
              timeout(time: 1, unit: 'HOURS') {
                waitForQualityGate abortPipeline: true
              }
            }
          }
    }
     post {
        success {
            jacoco(
                execPattern: '**/build/jacoco/*.exec',
                classPattern: '**/build/classes/java/main',
                sourcePattern: '**/src/main'
            )
        }
    }
}
