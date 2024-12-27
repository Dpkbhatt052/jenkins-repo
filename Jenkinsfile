pipeline {
    agent any
    environment {
        TEST = credentials('test')
    }
    stages {
        stage('Hello') {
            agent {
                docker {
                    image 'amazon/aws-cli'
                    args "--entrypoint=''"
                    reuseNode true
                }
            }
            steps {
                withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-login-new', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                      sh '''aws ecs register-task-definition --family Amazonlinux --cli-input-json file://taskdef.json --region us-east-1
                      '''
}
            }
        }
    }
} 
