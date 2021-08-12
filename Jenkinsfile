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
                sh 'cd /var/lib/jenkins/workspace/env/jenkins_test'
                sh 'cp /var/lib/jenkins/workspace/env/jenkins_test/* /var/lib/jenkins/workspace/env'
                sh 'docker build . -t imran319/sunny:v23'
            }
        }
        stage('Push') { 
            steps {
                echo 'testing the application'
                sh 'docker push imran319/sunny:v23'
            }
        }
        stage('Deploy') { 
            steps {
                echo 'deplying the application'
                sh 'docker run --rm -dit --name webapp23 --hostname webapp23 -p 9002:80 imran319/sunny:v23'
            }
        }
            stage('Testing') {
            steps {
                 sh 'curl ec2-18-188-207-46.us-east-2.compute.amazonaws.com:9002' 
            }
        }
    }
    post {
      // Clean after build
         always {
           cleanWs()
        }
    
    }
}
