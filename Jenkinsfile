pipeline {
    agent any

    stages {
        stage('install-pip-deps') {
            steps {
                echo 'installing all dependencies'
                git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
                sh 'ls -la'
                sh 'pip3 install -r requirements.txt'
            }
        }
        stage('deploy-to-dev') {
            steps {
                echo 'deploying to development environment'
                git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
                pm2 delete greetings-app-deploy-to-dev || true
            }
        }
        stage('tests-on-dev') {
            steps {
                echo 'testing in development environment'
                
            }
        }
        stage('deploy-to-staging') {
            steps {
                echo 'deploying to staging environment'
                git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
            }
        }
        stage('tests-on-staging') {
            steps {
                echo 'testing in staging environment'
                
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echo 'deploying to preproduction environment'
                git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
            }
        }
        stage('tests-on-preprod') {
            steps {
                echo 'testing in preproduction environment'
            }
        }
        stage('deploy-to-prod') {
            steps {
                echo 'deploying to production environment'
                git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
            }
        }
        stage('tests-on-prod') {
            steps {
                echo 'testing in production environment'
            }
        }
    }
}