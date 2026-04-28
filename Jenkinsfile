pipeline {
   agent any 

    tools {
        maven 'Maven'
    }

    stages {
        
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/kaitsanchez/gs-spring-boot.git', branch: 'main'
            }
        }
        stage('Build JAR') {
            steps {
                    sh 'mvn clean package -DskipTests'
            }
        }
        stage('Upload to Nexus') {
            steps {
                script {
                    sh 'mvn test'
                }
            }
        }
        stage('Archive JAR') {
            steps {
                withCredentials([usernamePassword:$PASSWORD --upload-file target/*.jar \
                http://localhost:8081/repository/maven-releases
                """
                }
            }
        }
    }
}
