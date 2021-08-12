pipeline {
    agent any 
    environment {
        NEW_VERSION = '1.3.0'
        GIT_URL = 'https://github.com/imranmohammadcan/jenkins_test.git'
    }
    stages {
        stage('Cloning our Git') {
            steps {
                  sh 'rm -rf dockertest1'
                   sh "git clone ${GIT_URL}"        
            }
        }
        stage('Build') { 
            steps {
               echo 'building the application..'
               echo "buliding version ${NEW_VERSION}"
            }
        }
        stage('Test') { 
            steps {
                echo 'testing the application'
            }
        }
        stage('Deploy') { 
            steps {
                echo 'deplying the application'
            }
        }
    }
}
