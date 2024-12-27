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
                sh '''
                aws ecs register-task-definition --family Amazonlinux --cli-input-json taskdef.json --region us-east-1
                '''
            
            }
        }
    }
}
