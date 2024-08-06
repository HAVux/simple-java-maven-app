pipeline {
    agent any
    tools {
        maven 'maven'
    }
    options {
        skipStagesAfterUnstable()
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
                    junit skipPublishingChecks: true, stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}