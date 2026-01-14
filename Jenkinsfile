pipeline {
    agent {
        node {
            label 'AGENT-1'
            
        }
    }
    environment { 
        COURSE = 'jenkins'
    }
    stages {
        stage('Build') {
            steps {
                sh """
                    echo "Building"
                    echo $COURSE
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