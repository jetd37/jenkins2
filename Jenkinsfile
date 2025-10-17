pipeline {
    agent any
    environment {
        URL1 = 'https://github.com/jetd37/jenkins2.git'
        CREDENTIALSID = 'jetd'
    }
    stages {
        stage('Clone repository') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        credentialsId: "${CREDENTIALSID}",
                        url: "${URL1}",
                    ]]
                ])
                echo 'Cloning repository...'
                sh "printenv"
            }
        }

        stage('Readfile and print its content') {
            steps {
                echo 'Reading file... and Ready to print its content'
                script {
                    def content = readFile 'server.csv'
                    def lines = content.split(/\r?\n/)
                    lines.each { line ->
                        echo line
                    }
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'cat server.csv'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh 'ls -la'
            }
        }
    }
}