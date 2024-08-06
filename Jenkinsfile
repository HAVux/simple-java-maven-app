pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                //-B: Batch mode (non-interactive mode)
                //-DskipTests: skip the execution of tests during the build
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}