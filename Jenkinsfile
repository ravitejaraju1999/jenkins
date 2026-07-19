pipeline {
    // this are pre build sesion
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
        timeout(time: 10, unit: 'MINUTES') // Set a timeout for the entire pipeline
        disableConcurrentBuilds() // Prevent concurrent builds of the same job
    }
    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Branch to build')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Deploy the application after build')
        choice(name: 'DEPLOY_ENV', choices: ['dev', 'staging', 'production'], description: 'Select the deployment environment')
        password(name: 'DEPLOY_PASSWORD', defaultValue: '', description: 'Password for deployment')
    }
    // Define the stages of the pipeline

    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                       echo "Building the project for ${COURSE}"
                       sleep 10
                       env

                       echo "Building branch: ${params.BRANCH_NAME}"
                       echo "Deploying: ${params.DEPLOY}"
                       echo "Deploying to: ${params.DEPLOY_ENV}"
                       echo "Deployment password: ${params.DEPLOY_PASSWORD}"

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
            // input {
            //     message "Should we continue?"
            //     ok "Yes, we should."
            //     submitter "alice,bob"
            //     parameters {
            //         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
            //     }
            // }
            when {
                expression {
                    "$params.DEPLOY" == "true"
                }
            }


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
