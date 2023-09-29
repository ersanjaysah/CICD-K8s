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
        
        stage('MODIFIED IMAGE TAG') {
            steps {
                sh '''
                   sed "s/image-name:latest/$JOB_NAME:v1.$BUILD_ID/g" playbooks/dep_svc.yml
                   sed -i "s/image-name:latest/$JOB_NAME:v1.$BUILD_ID/g" playbooks/dep_svc.yml
                   sed -i "s/IMAGE_NAME/$JOB_NAME:v1.$BUILD_ID/g" webapp/src/main/webapp/index.jsp
                   '''
            }            
        }

        stage('BUILD') {
            steps {
                sh 'mvn clean install package'
            }
        } 
    }
}