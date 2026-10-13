pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Pulling latest source code from repository...'
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling Java Application with Maven...'
                sh 'mvn compile'
            }
        }

        stage('Package & Test') {
            steps {
                echo 'Packaging Application into JAR...'
                sh 'mvn clean package'
            }
        }

        stage('Verify') {
            steps {
                echo 'Verifying compiled JAR executable...'
                sh 'java -jar target/jenkins-lab-1.0.jar'
            }
        }
    }

    post {
        always {
            echo 'CI Build finished.'
        }
        success {
            echo 'Jenkins CI Pipeline: BUILD SUCCESS!'
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
        }
        failure {
            echo 'Jenkins CI Pipeline: BUILD FAILED!'
        }
    }
}
