pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage('Build') { 
            steps {
                //-B: Batch mode (non-interactive mode)
                //-DskipTests: skip the execution of tests during the build
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surfire-report/*.xml'
                }
            }
        }
    }
}