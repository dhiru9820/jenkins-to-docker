pipeline{
    agent any
    tools {
        maven 'MAVEN'
    }
    stages {
        stage('Build Maven') {
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Githubcredential', url: 'https://github.com/Saurav0310/Jenkins-docker2.git']]])
                bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                  bat 'docker build -t devopsimage/my-app-1 .'
                }
            }
        }
    }
}
