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
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Build') {
            steps {
                sh """
                    echo "Building"
                    echo $COURSE
                    sleep 10
                    echo "Hello ${params.PERSON}"
                    echo "Biography: ${params.BIOGRAPHY}"
                    echo "Toggle: ${params.TOGGLE}"
                    echo "Choice: ${params.CHOICE}"
                    echo "Password: ${params.PASSWORD}"
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