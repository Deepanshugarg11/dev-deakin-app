pipeline {
    agent any

    environment {
        NODEJS_HOME = tool 'NodeJS'
        PATH = "$NODEJS_HOME/bin:$PATH"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Deepanshugarg11/dev-deakin-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Code Quality Analysis') {
            steps {
                sh 'sonar-scanner'
            }
        }

        stage('Dockerize') {
            steps {
                sh 'docker build -t dev-deakin-app .'
            }
        }

        stage('Deploy to Server') {
            steps {
                sh 'docker run -d -p 3000:3000 dev-deakin-app'
            }
        }
    }
}

