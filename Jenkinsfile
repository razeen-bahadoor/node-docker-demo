@Library("jenkins-shared-libs@main") _

pipeline {
    agent {
        kubernetes {
          yaml """
          apiVersion: v1
          kind: Pod
          metadata: {}
          spec:
            serviceAccount: jenkins-worker
            affinity:
              nodeAffinity:
                requiredDuringSchedulingIgnoredDuringExecution:
                            nodeSelectorTerms:
                              - matchExpressions:
                                  - key: role
                                    operator: In
                                    values:
                                      - worker
            containers:
            - name: jnlp
              image: jenkins/jnlp-slave:alpine
              env:
                - name: GIT_SSL_NO_VERIFY
                  value: "true"
            - name: kaniko
              image: gcr.io/kaniko-project/executor:debug
              imagePullPolicy: Always
              command:
              - /busybox/cat
              tty: true
            - name: ubuntu
              image: ubuntu:22.04
              tty: true
              env:
               - name: GIT_SSL_NO_VERIFY
                 value: "true"
          """
        }
      }
      parameters {
        choice(name: 'TARGETENV', choices: ['AUTO','DEV','SIT','UAT','PROD'], description: 'Target environment to deploy to')
      }
    stages {
        stage('Code Checkout') {
            steps {
                container('ubuntu'){
                script {
                  def workingDir = checkoutCode("https://github.com/razeen-bahadoor/node-docker-demo.git", "master")
                  echo $workingDir
                }
              }
            }
        }
    }
}