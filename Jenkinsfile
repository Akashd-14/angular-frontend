pipeline {
    agent any
    stages {
        stage('pull'){
            steps {
                git branch: 'dev', url: 'https://github.com/Akashd-14/angular-frontend.git'
            }
        }
        stage('build'){
            steps {
                sh '''npm install
                    ng build '''
            }
        }
        stage('deploy'){
            steps {
                sh '''
                    withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
    // some block
}
                    aws s3 cp --recursive dist/angular-frontend/ s3://frontend-project-bkt/
                '''
            }
        }
    }
}