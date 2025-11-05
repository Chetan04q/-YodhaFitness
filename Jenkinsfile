pipeline {
    // Run on any available Jenkins agent
    agent any

    // Define the stages of your pipeline
    stages {

        // STAGE 1: Get the code from your Git repository
        stage('Checkout Code') {
            steps {
                // This step is configured in the Jenkins UI
                echo 'Checking out code...'
            }
        }

        // STAGE 2: Build the new Docker images
        stage('Build') {
            steps {
                echo 'Building images with docker-compose...'
                // This reads your 'docker-compose.yml' and builds
                sh 'docker-compose build'
            }
        }

        // STAGE 3: Stop old containers and run the new ones
        stage('Deploy') {
            steps {
                echo 'Stopping old containers...'
                // This stops and removes any containers defined
                sh 'docker-compose down'

                echo 'Starting new containers...'
                // This starts your new, freshly built containers
                sh 'docker-compose up -d'
            }
        }
    }

    // This block runs after all stages
    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}