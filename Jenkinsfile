pipeline {
   agent any 

    tools {
        maven 'maven3'  
        jdk 'jdk17'
    }

    stages {
        
        stage('Checkout') {
            steps {
                git url: 'https://github.com/kaitsanchez/springboot-jenkins-midterm.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                script {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh 'mvn test'
                }
            }
        }
        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
