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
    }
}
