pipeline {

    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    triggers {
        githubPush()
    }

    stages {

        stage('Welcome') {
            steps {
                echo 'Welcome to Jenkins Pipeline!'
                echo "Build Number: ${BUILD_NUMBER}"
            }
        }

        stage('Clean') {
            steps {
                bat "mvn clean"
            }
        }

        stage('Compile') {
            steps {
                bat "mvn compile"
            }
        }

        stage('Install') {
            steps {
                bat "mvn install"
            }
        }

        stage('Test') {
            steps {
                bat "mvn test"
            }
        }

        stage('Package') {
            steps {
                bat "mvn package"
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                echo 'Tomcat deployment step'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
