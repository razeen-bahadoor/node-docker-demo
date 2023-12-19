@Library("jenkins-shared-libs@main") _

pipeline {
    agent any
    stages {
        stage('Code Checkout') {
            steps {
                script {
                  def workingDir = checkoutCode("https://github.com/razeen-bahadoor/node-docker-demo.git", "master")
                  echo $workingDir
                }
            }
        }
    }
}