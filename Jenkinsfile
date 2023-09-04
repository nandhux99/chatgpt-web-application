pipeline {
    agent any
     environment {
                   key = credentials('openAI')
                }
    stages {
        stage('Code fetch') {
            steps {
                git url:'https://github.com/nandhux99/chatgpt-web-application.git',branch:'master'
            }
        }
        stage('build and test') {
            steps {
                sh 'sudo docker build . -t myapp'
            }
        }
        stage('Deploy'){
            steps {
                withCredentials([string(credentialsId: 'openAI', variable: 'OPENAI_API_KEY')]) {
                                sh 'docker run -d --name myapp -p 8081:3001 myapp'
                                
                        }
                    
            }
        }
    }
}
