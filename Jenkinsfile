
pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['staging', 'production'])
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Quality') {
            parallel {
                stage('Build') {
                    steps {
                        bat 'echo Build'
                    }
                }

                stage('Lint') {
                    steps {
                        bat 'echo Lint'
                    }
                }
            }
        }

        stage('Approve') {
            when {
                expression {
                    params.ENVIRONMENT == 'production'
                }
            }
            steps {
                input message: 'Do you want to proceed with production deployment?',
                      ok: 'Proceed'
            }
        }

        stage('Test') {
            steps {
                bat 'echo Test'
            }
        }

        stage('Package') {
            steps {
                bat 'echo Package'
            }
        }
    }
}

