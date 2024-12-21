pipeline {
    agent { node { label 'Agent-1' } } 
    stages {
        stage('install dependencies') {
            
            steps {
                sh 'npm install'
            }
        }
        stage('Unit Test') {
            steps {
                echo "unit testing"
            }
        }
        //sonar scanner command expects sonar-project.properties should be available
        stage('Sonar scan') {
            steps {
                sh 'ls -ltr'
                sh 'sonar-scanner'
        
            }
        }
        stage('Build') {
            steps {
                sh 'ls -ltr'
                sh 'zip -r ./*'

            }
        }
        stage('Deploy') {
            steps {
                sh 'ls -ltr'
                echo "Deploying"
        
            }
        } 
    }
    post{
        always{
            echo 'cleaning up workspace'
            deleteDir()
        }
    }
}

