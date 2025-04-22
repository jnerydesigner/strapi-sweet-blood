pipeline {
    agent any
    tools {
        nodejs 'NodeJS_22'
    }
     environment {
        POSTGRES_USER     = credentials('DATABASE_USERNAME')
        POSTGRES_PASSWORD = credentials('DATABASE_PASSWORD')
        POSTGRES_DB       = credentials('DATABASE_NAME')
    }
    stages {
        stage('Check Node Version') {
            steps {
                script {
                    def nodeVersion = sh(script: 'node -v', returnStdout: true).trim()
                    echo "Node.js version: ${nodeVersion}"
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'yarn install'
            }
        }
        stage('Build StrapiCMS Blood Sweet') {
            steps {
                script {
                    sh 'yarn build'
                }
            }
        }
    }
}
