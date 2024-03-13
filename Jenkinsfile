pipeline {
    agent any

    stages {
        stage("code-checkout") {
            steps {
                script {
                    git url: "https://github.com/ash2code/simple-java-maven-app.git",
                    branch: "master"
                }
            }
        }

        stage("build") {
            steps {
                sh "mvn clean package"
            }
        }

        stage("test") {
            steps {
                sh "mvn test"
            }
        }

    post {
        success {
            echo "Pipeline succeeded! You can deploy now."
        }
        failure {
            echo "Pipeline failed. Please check logs for details."
        }
    }
}

