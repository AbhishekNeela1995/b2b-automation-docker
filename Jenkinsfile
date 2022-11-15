pipeline {
    // master executor should be set to 0
    agent any
    stages {
        stage('Build Jar') {
            steps {
                //sh
                bat "mvn clean package -DskipTests"
            }
        }
        stage('Build Image') {
            steps {
                //sh
                bat "docker build -t 'abhishekneela/b2b-automation-docker' ."
            }
        }
        stage('Push Image') {
            steps {
			    withCredentials([usernamePassword(credentialsId: 'b2bdockerhub', passwordVariable: 'Abhitha@143', usernameVariable: 'abhishekneela')]) {
                    //sh
			        bat "docker login --username=${user} --password=${pass}"
			        bat "docker push abhishekneela/b2b-automation-docker:latest"
			    }                           
            }
        }
    }
}
