pipeline{
    agent any

    stages{
        stage("Verify Branch"){
            steps{
                echo "$GTI_BRANCH"
            }
        }

        stage("Docker Build"){
            steps{
                sh(script: 'docker conpose build')
            }
        }
    }
}
