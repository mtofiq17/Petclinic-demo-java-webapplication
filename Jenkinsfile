pipeline {
    agent any

    tools {
        jdk 'jdk11'
        maven 'maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'div-1', url: 'https://github.com/mtofiq17/Petclinic-demo.git'
            }
        }
        
        stage('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }

        stage('Package') {
            steps {
                sh "mvn clean package -DskipTests=true"
            }
        }

        stage('Deploy') {
            steps {
                // Ensure the Jenkins user has sudo access without password for this command
                script {
                    sh "sudo cp target/*.war /opt/apache-tomcat-9.0.89/webapps"
                }
            }
        }
    }
}
