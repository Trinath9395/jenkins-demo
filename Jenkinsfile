pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT = 'expense'
        COMPONENT = 'BACKEND'
    }
    options {
        disableConcurrentBuilds()
        timeout(time: 30, unit: 'MINUTES')
    }
    parameters{
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                      echo "Hello, this is build step"
                      echo "Project: $PROJECT"
                      sleep 15 

                      echo "Hello ${params.PERSON}"
                      echo "Biography: ${params.BIOGRAPHY}"
                      echo "Toggle: ${params.TOGGLE}"
                      echo "Choice: ${params.CHOICE}"
                      echo "Password: ${params.PASSWORD}"
                    """
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh """ 
                      echo "Hello, this is test stage"
                    """
                }
            }
        }
        stage('Deploy') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
            }
            steps {
                script {
                    sh """ 
                      echo "Hello, this is Deploy stage" 
                    """
                }
            }
        }
    }
    post{
        always {
            echo "I will run always say hello again"
        }
        failure {
            echo "I will run pipeline failed"
        }
        success {
            echo "I will run when pipeline is success"
        }
    }
        

}