pipeline {
    agent any

    tools {
        maven 'my-maven' // Ensure 'my-maven' is correctly configured in Jenkins
    }

    stages {
        stage("build jar") {
            steps {
                echo 'Building the application...'
                sh 'mvn package'
            }
        }

        stage("build image") {
            steps {
                echo 'Building the docker image...'
                withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh 'docker build -t galalshalaby/e-commerce:2.0 .'
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push galalshalaby/e-commerce:2.0'
                }
            }
        }

        stage("test") {
            steps {
                echo 'Testing the application...'
                // Add test steps here
            }
        }

        stage("deploy") {
            steps {
                echo 'Deploying the application...'
                // Add deployment steps here
            }
        }
    }
}
