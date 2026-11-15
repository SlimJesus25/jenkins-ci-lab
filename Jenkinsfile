
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Preparing application...'

                sh 'ls -la'
                sh 'mkdir -p build'

                echo 'Build stage completed!'
            }
        }

        stage('Test') {
            steps {
                echo 'Executing application tests...'

                sh 'grep -q "Hello from GitHub!" app/hello.sh'

                echo 'Tests passed!'
            }
        }

        stage('Package') {
            steps {
                echo 'Creating application package...'

                sh 'tar -czf app.tar.gz app/'

                archiveArtifacts artifacts: 'app.tar.gz',
                                 fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline completed successfully!'
        }

        failure {
            echo 'CI Pipeline failed!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
