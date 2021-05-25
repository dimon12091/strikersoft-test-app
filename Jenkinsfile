pipeline {

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
                    dockerImage = docker.build jenkins-test + “$BUILD_NUMBER”
                }
            }
        }
    }
}