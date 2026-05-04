pipeline {
    agent any
    
    tools {
        maven 'M3' // This name must exactly match the name you typed in Jenkins Tools
    }

    stages {
        stage('Checkout') {
            steps { 
                git 'https://github.com/parnikanag/maven-demo' 
            }
        }
        stage('Build') {
            steps { 
                sh 'mvn clean package' 
            }
        }
        stage('Test') {
            steps { 
                sh 'mvn test' 
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}
