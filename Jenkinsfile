//

pipeline {
    agent any

    environment{
        PATH='/opt/homebrew/opt/openjdk/bin:/opt/homebrew/opt/openjdk/bin:/usr/local/bin/node:/Library/Frameworks/Python.framework/Versions/3.12/bin:/opt/homebrew/bin:/opt/homebrew/sbin:/usr/local/bin:/System/Cryptexes/App/usr/bin:/usr/bin:/bin:/usr/sbin:/sbin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/local/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/bin:/var/run/com.apple.security.cryptexd/codex.system/bootstrap/usr/appleinternal/bin'
    }
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
                dir('python-greetings'){
                sh 'git switch -d 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51'
                sh 'pm2 delete greetings-app-dev || true'
                sh 'pm2 start app.py --name greetings-app-dev -- --port 7001'
                }
            }
        }
        stage('tests-on-dev') {
            steps {
                echo 'testing in development environment'
                git branch: 'main', url: 'https://github.com/mtararujs/course-js-api-framework'
                sh 'npm install'
                sh 'npm run greetings greetings_dev'
                
            }
        }
        stage('deploy-to-staging') {
            steps {
                echo 'deploying to staging environment'
                git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
                dir('python-greetings'){
                sh 'git switch -d 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51'
                sh 'pm2 delete greetings-app-staging || true'
                sh 'pm2 start app.py --name greetings-app-staging -- --port 7002'
                }
            }
        }
        stage('tests-on-staging') {
            steps {
                echo 'testing in staging environment'
                git branch: 'main', url: 'https://github.com/mtararujs/course-js-api-framework'
                sh 'npm install'
                sh 'npm run greetings greetings_stg'
            }
        }
        stage('deploy-to-preprod') {
            steps {
                echo 'deploying to preproduction environment'
                git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
                dir('python-greetings'){
                sh 'git switch -d 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51'
                sh 'pm2 delete greetings-app-preprod || true'
                sh 'pm2 start app.py --name greetings-app-preprod -- --port 7003'
                }
            }
        }
        stage('tests-on-preprod') {
            steps {
                echo 'testing in preproduction environment'
                git branch: 'main', url: 'https://github.com/mtararujs/course-js-api-framework'
                sh 'npm install'
                //sh 'npm run greetings greetings_preprod'
                //neeksistē lol!
            }
        }
        stage('deploy-to-prod') {
            steps {
                echo 'deploying to production environment'
                git branch: 'main', url: 'https://github.com/mtararujs/python-greetings'
                dir('python-greetings'){
                sh 'git switch -d 4e911440a9886c7c26ccbb4eb55f0bc2a5067b51'
                sh 'pm2 delete greetings-app-prod || true'
                sh 'pm2 start app.py --name greetings-app-prod -- --port 7004'
                }
            }
        }
        stage('tests-on-prod') {
            steps {
                echo 'testing in production environment'
                git branch: 'main', url: 'https://github.com/mtararujs/course-js-api-framework'
                sh 'npm install'
                sh 'npm run greetings greetings_prod'
            }
        }
    }
}