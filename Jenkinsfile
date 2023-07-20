pipeline {
    agent any
      tools {
    jdk 'JDK17'
    maven 'maven 3.9.3'
  }
//     triggers {
//         pollSCM('* * * * *')
//     }
    stages {

//         stage('Compile Stage') {
//             steps {
//                 echo '::::: Hello, Compile  :::::'
//                 sh 'mvn clean compile'
//             }
//         }

        stage('mvn Build Stage') {
            steps {
                echo '::::: Hello, mvn Build stage  :::::'
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Ashish-rajpoot/cicd.git']])
                sh 'mvn clean install -DskipTests'
            }
        }
       /*  stage('Docker Build Stage') {
            steps {
                echo '::::: Hello, Docker Build stage  :::::'
                sh 'docker image build -t cicd .'
            }
        }
        stage('Tag docker image'){
            steps {
                sh 'docker tag cicd ashish142/cicd:1.0.0'
            }
        }
        stage('Push docker image'){
            steps {
                sh 'sudo docker push ashish142/cicd:1.0.0'
            }
        }
        stage('Deploy Stage') {
            steps {
                echo 'Hello, Docker Deployment.'
                sh '''
                 (if  [ $(docker ps -a | grep cicd | cut -d " " -f1) ]; then \
                        echo $(docker rm -f cicd); \
                        echo "---------------- successfully removed cicd ----------------"
                     else \
                    echo OK; \
                 fi;);
            docker container run --restart always --name cicd -p 8081:8081 -d cicd
            '''
            }
        }
        */
    }

}