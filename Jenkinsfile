pipeline {

agent any

stages {

stage('Clone Code') {

steps {

git url: 'https://github.com/ankitamohanty1509/jenkins-kubernetes.git', branch: 'main'

}

}

stage('Build Docker Image') {

steps {

sh 'docker build -t ankitamohanty1509/flask-ci-cd:latest .'

}

}

stage('Push to Docker Hub') {

steps {

withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {

sh 'docker push ankitamohanty1509/flask-ci-cd:latest'

}

}

}

stage('Deploy to Kubernetes') {

steps {

sh 'kubectl apply -f k8s-deployment.yaml'
}
}
}
}
