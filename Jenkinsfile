pipeline {
    agent { label 'AGENT-1' }
    environment {
        PROJECT = 'expense'
        COMPONENT = 'backend'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                      echo "Hello, this is build step"
                      echo "Project: $PROJECT"
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