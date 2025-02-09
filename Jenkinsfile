pipeline {
    agent any

    stages {
        stage("Verify Branch") {
            steps {
                echo "${env.GIT_BRANCH}"
            }
        }

        stage("Docker Build") {
            steps {
                sh 'docker compose build'
            }
        }

        stage("Start App") {
            steps {
                sh 'docker --version'
                sh 'docker compose --version'
                sh 'docker compose up -d'
            }
        }

        stage("Run Tests") {
            steps {
                sh "pytest ./tests/test_sample.py"
            }
            post {
                success {
                    echo "Test Passed :)"
                }
                failure {
                    echo "Test Failed :("
                }
            }
        }
    }

    post {
        always {
            echo "Cleaning up..."
            sh 'docker compose down'
        }
    }
}
