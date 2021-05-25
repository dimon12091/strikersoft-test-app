pipeline {
    environment {
        imagename = "yenigul/hacicenkins"
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

      stage('Fire Up docker-compose') {
        steps {
            sh "ls"
            step([$class: 'DockerComposeBuilder', dockerComposeFile: 'docker-compose.yml', option: [$class: 'StartAllServices'], useCustomDockerComposeFile: false])
        }
      }
    }
}
