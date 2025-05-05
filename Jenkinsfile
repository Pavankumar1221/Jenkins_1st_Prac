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
                echo 'Starting local web server on port 8081...'
                sh '''
                    mkdir -p /var/jenkins_home/html-deploy
                    cp index.html /var/jenkins_home/html-deploy/
                    cd /var/jenkins_home/html-deploy
                    nohup python3 -m http.server 8081 &
                '''
                echo 'App deployed at http://<jenkins-server-ip>:8081'
            }
        }
    }
}
