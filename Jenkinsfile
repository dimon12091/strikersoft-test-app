pipeline {
    environment {
    imagine = "wolfmoon69/testapp"
    registryCredential = ‘dockerhub’
    dockerImage = ‘’
    }
    agent any
    stages {
      stage("SCM") {
        steps {
            checkout([
              $class: 'GitSCM',
              branches: [[name: 'master']],
              userRemoteConfigs: [[credentialsId: 'github-ssh-key', url: 'git@github.com:dimon12091/strikersoft-test-app.git']]
            ])
            }
        }

        stage("Docker build") {
            steps{
                script {
                    dockerImage = docker.build imagine + “$BUILD_NUMBER”
                }
            }
        }
        stage("Push Image to Docker Hub") {
            steps{
                script {
                    docker.withRegistry( ‘’, registryCredential ) {
                    dockerImage.push()
                    dockerImage.push(‘latest’)
            }}
        }}
    }
}