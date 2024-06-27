pipeline {
    agent any
    environment {
        PATH = "/opt/maven3.9/bin/:$PATH"
    }
    stages {
        
        stage('GitClone') {
            steps {
                git branch: 'main', url: 'https://github.com/devopsjune2024/june25maven.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
