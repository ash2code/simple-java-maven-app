pipeline {
    agent any

    tools {
        maven "m3"
    }

    stages {
        stage("code-checkout") {
            steps {
                script {
                    git url: "https://github.com/ash2code/simple-java-maven-app.git", branch: "master"
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

        stage("code-test") {
            steps {
                script {
                    sh "mvn test"
                }
            }
        }

        stage("Sonar-Analysis") {
            steps {
                withSonarQubeEnv('sonarqube-analysis') {
                    sh '''mvn clean verify sonar:sonar \
                       -Dsonar.projectKey=java-demo \
                       -Dsonar.projectName='java-demo' \
                       -Dsonar.host.url=http://54.82.198.143:9000 \
                       -Dsonar.login=sqp_d01fd5f4d7f7e063efdda1b72001979cd16a24f6'''
                }
            }
        }

        stage("Docker-Build") {
            steps {
                script {
                    sh "docker build -t ash2code/mvn-project ."
                }
            }
        }

        stage("Docker-Push") {
            steps {
                script {
                    sh "docker push ash2code/mvn-project "
                }
            }
        }
    }
}
     
