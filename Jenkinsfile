pipeline {
    agent any
    
    tools {
        maven 'M3' 
    }

    stages {
        stage('Checkout') {
            steps { 
               git url:'https://github.com/parnikanag/maven-demo' , branch: 'main'
            }
        }
        stage('Build') {
            steps { 
                // Skips test execution during the build phase to save time
                sh 'mvn clean package -DskipTests' 
            }
        }
        stage('Test') {
            steps { 
                // Runs the tests but ignores failures so Jenkins can record the results
                sh 'mvn test -Dmaven.test.failure.ignore=true' 
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}
