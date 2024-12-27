pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                sh '''
                cat > Dockerfile <<EOF
FROM python:3.12
WORKDIR /usr/local/app
EOF
docker build -t python .
docker images
'''

                
            }
        }
    }
}
