pipeline {
    agent {
        node {
            label 'AGENT-1'
            
        }
    }
    environment { 
        COURSE = 'jenkins'
    }
    options {
        timeout(time: 1, unit: 'HOURS') 
        disableConcurrentBuilds()
    }
    stages {
        stage('Build') {
            steps {
                sh """
                    echo "Building"
                    echo $COURSE
                    sleep 10
                    env
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
        aborted {
            echo 'pipeline is aborted'
        }
    }
}