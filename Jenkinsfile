pipeline {
    agent any

    stages {
        stage('Remove') {
            steps {
                sh 'rm -rf *'
            }
        }
        stage('Pull') {
            steps {
                git branch: 'main', url: 'https://github.com/Akashd-14/front.git'
            }
        }
        stage('build') {
            steps {
                sh '''
                npm install
                ng build
                '''
            }
        }
        stage('Deploy') {
            steps {
            withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws cred', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
       sh 'aws s3 cp --recursive dist/angular-frontend/ s3://cbz-frontend-project-aa/'
              }
            }
        }
    }
}
