pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                    cd /var/jenkins_home/workspace/flask-app
                    docker-compose build web
                '''
            }
        }
        
        stage('Test') {
            steps {
                sh '''
                    cd /var/jenkins_home/workspace/flask-app
                    which python3
                    python3 --version
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                    pytest --cov=app
                '''
            }
        }
        
        stage('Deploy') {
            steps {
                sh '''
                    cd /var/jenkins_home/workspace/flask-app
                    docker-compose up -d web
                '''
            }
        }
    }

    post {
        always {
            sh '''
                cd /var/jenkins_home/workspace/flask-app
                docker-compose down
            '''
        }
        failure {
            sh '''
                cd /var/jenkins_home/workspace/flask-app
                docker-compose logs web
            '''
        }
    }
} 