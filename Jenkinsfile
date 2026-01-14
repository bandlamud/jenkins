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
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Toggle this value')
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
                    echo "Deploy: ${params.DEPLOY}"
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
            // input {
            //     message "Should we continue?"
            //     ok "Yes, we should."
            //     submitter "alice,bob"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            // }
            when {
                expression { "$params.DEPLOY"  == "true" }

                }
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