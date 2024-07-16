pipeline {
    agent any

    environment {
        NVD_API_KEY = 'f0041770-b1c8-438a-8a77-583e617fb188'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }
        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: "--nvdApiKey ${env.NVD_API_KEY}"
            }
        }
    }
}
