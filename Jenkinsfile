pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
    post{
        always{
            echo 'This will always run after the stages are complete.'
            cleanWs()

        }
        success{
            echo 'This will run only if the pipeline succeeds.'
        }
        failure{
            echo 'This will run only if the pipeline fails.'
        }
    }
}
