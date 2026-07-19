pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        // Define environment variables here
        COURSE = "Jenkins Pipeline"
    }
    options {
        timeout(time: 10, unit: 'SECONDS') // Set a timeout for the entire pipeline
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                       echo "Building the project for ${COURSE}"
                       sleep 10

                    """
                    
                }
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
        aborted{
            echo 'The pipeline is aborted.'
        }
    }
}
