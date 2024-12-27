pipeline {
    agent any
    environment {
        TEST = credentials('test')
    }
    stages {
        stage('W/o Docker') {
            steps {
                sh '''
                   ls -la
                   touch dpk.txt
                   echo $TEST
                   '''
            }
            
        }
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
                aws ecs register-task-definition --family Amazonlinux --cli-input-json 
                '''
            
            }
        }
    }
}
