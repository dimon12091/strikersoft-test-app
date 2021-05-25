pipeline {
    environment {
        registryCredential = 'dockerhub'
        dockerImage = ''
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
                    sh "ls"
                    dockerImage = docker.build("wolfmoon69/bob")
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