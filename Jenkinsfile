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
    }
}

