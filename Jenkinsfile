pipeline {
    agent {
        node {
            label 'AGENT-1'
            
        }
    }
    stages {
        stage('Build') {
            steps {
                sh """
                    echo "Building"
                """
            }
        }
        stage('Test') {
            steps {
                sh """
                    echo "Testing"
                """
            }
        }
        stage('Deploy') {
            steps {
                sh """
                    echo "Deploying"
                """
            }
        }
    }
     post { 
        always { 
            echo 'I will always say Hello again!'
            cleanWs()
        }
        success {
            echo 'i will run if success'
        }
        failure {
            echo 'i will run if failure'
        }
    }
}