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

//         stage("Docker build") {
//           steps {
//             script {
//               dir ("mongo-backup") {
//                  sh 'ls'
//                  def image = docker.build("docker-repository.strikersoft.dev/careflow/mongo42-backup:$TAG")
//                  docker.withRegistry('https://docker-repository.strikersoft.dev', 'docker-registry-careflow') {
//                     image.push("${env.BUILD_NUMBER}")
//                  // image.push("latest")
//                  }
//                 }
//               }
//           }
//         }
      }
}