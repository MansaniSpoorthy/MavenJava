pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {

        stage('Welcome') {
            steps {
                echo 'Welcome to Jenkins Pipeline!'
                echo "Build Number: ${BUILD_NUMBER}"
            }
        }

        stage('Git Repo & Clean') {
            steps {
                deleteDir()
                bat "git clone -b master https://github.com/MansaniSpoorthy/MavenJava.git mavenjava"
                bat "mvn clean -f mavenjava"
            }
        }

        stage('Compile') {
            steps {
                bat "mvn compile -f mavenjava"
            }
        }

        stage('Install') {
            steps {
                bat "mvn install -f mavenjava"
            }
        }

        stage('Test') {
            steps {
                bat "mvn test -f mavenjava"
            }
        }

        stage('Package') {
            steps {
                bat "mvn package -f mavenjava"
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
