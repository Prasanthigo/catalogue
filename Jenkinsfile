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
                sh 'zip -r catalogue.zip ./* --exclude=.git --exclude=.zip'

            }
        }
        stage('Publish Artifact') {
            steps {
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: '18.234.87.21:8081/',
                    groupId: 'com.roboshop',
                    version: '1.0.0',
                    repository: 'catalogue',
                    credentialsId: 'Nexus',
                    artifacts: [
                        [artifactId: catalogue,
                        classifier: '',
                        file: 'catalogue.zip',
                        type: 'zip']
        ]
     )
                
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

