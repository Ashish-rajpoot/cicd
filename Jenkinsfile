pipeline {
    agent any
    stages {
        stage('Compile Stage') {
            steps {
                echo '::::: Hello, Compile  :::::'
                sh 'mvn clean compile'
            }
        }

        stage('mvn Build Stage') {
            steps {
                echo '::::: Hello, mvn Build stage  :::::'
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Docker Build Stage') {
            steps {
                echo '::::: Hello, Docker Build stage  :::::'
                sh 'docker image build -t cicd .'
            }
        }

        stage('Tag docker image') {
            steps {
                sh 'docker tag cicd ashish142/cicd:1.0.0'
            }
        }

        stage('Push docker image') {
            steps {
                sh 'docker push ashish142/cicd:1.0.0'
            }
        }

        stage('Deploy Stage') {
            steps {
                echo 'Hello, Docker Deployment.'
                bat '''
                    if exist cicd (
                        docker rm -f cicd
                        echo ---------------- successfully removed cicd ----------------
                    ) else (
                        echo OK
                    )
                    docker container run --restart always --name cicd -p 8081:8081 -d cicd
                '''
            }
        }
    }
}
