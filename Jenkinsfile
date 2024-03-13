pipeline {
    agent any

    tools {
        maven "m3"
    }

    stages {
        stage("code-checkout") {
            steps {
                script {
                    git url: "https://github.com/ash2code/simple-java-maven-app.git",
                    branch: "master"
                }
            }
        }

        stage("code-build") {
            steps {
                script {
                    sh "mvn clean package"
                }
            }
        }

        stage ("code-test") {
            steps {
                script {
                    sh "mvn test"
                }
            }
        }
    }
}


       
