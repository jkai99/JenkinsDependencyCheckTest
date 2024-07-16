pipeline {
    agent any
    environment {
        NVD_API_KEY = credentials('nvd-api-key')
    }
    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/jkai99/JenkinsDependencyCheckTest.git', branch: 'master', credentialsId: 'jenkins-PAT'
            }
        }
        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'owasp'
            }
        }
    }
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}