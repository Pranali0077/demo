pipeline {
    agent any
    parameters {
        choice (name: 'Environment', choices: ['staging', 'production'],description: 'Target')
    }    
    stages ('Tests') {
        parallel {
            stage('Unit') { steps {bat 'echo Unit tests' } }
            stage('Integration') { steps { bat 'echo Integration tests' } }
        }       
    }
}
