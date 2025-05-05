pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Pavankumar1221/Jenkins_1st_Prac.git'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing index.html exists...'
                sh 'test -f index.html'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting local web server...'
                sh '''
                    mkdir -p ~/html-deploy
                    cp index.html ~/html-deploy/
                    cd ~/html-deploy
                    nohup python3 -m http.server 8080 &
                '''
                echo 'App deployed at http://localhost:8080'
            }
        }
    }
}
