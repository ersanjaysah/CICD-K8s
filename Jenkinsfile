pipeline {
    agent any

    stages {
        stage('clean workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Git Checkout') {
            steps {
                echo 'Cloning the Project from Github to Jenkins Workspace'
                git 'https://github.com/ersanjaysah/CICD-K8s.git'
            }
        }
        
    }
}