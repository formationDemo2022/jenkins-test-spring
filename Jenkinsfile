pipeline {
    agent any
    options {
        skipDefaultCheckout()
    }
    stages {
        stage('SCM') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            parallel {
                stage('Compile') {
                    agent {
                        docker {
                            image 'maven:3.6.0-jdk-8'
                            reuseNode true
                        }
                    }
                    steps {
                        bat 'mvn clean compile'
                    }
                }
            }
        }
    }
}
