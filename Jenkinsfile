pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Carnage725/devops-exp06'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
        success {
            echo 'BUILD SUCCESS: All stages completed successfully.'
        }
        failure {
            echo 'BUILD FAILURE: One or more stages failed. Check logs above.'
        }
    }
}
