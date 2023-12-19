@Library("jenkins-shared-libs@main") _

String runtime = "nodejs"

properties([
  parameters([
        choice(name: 'TARGETENV', choices: ['AUTO','DEV','SIT','UAT','PROD'], description: 'Target environment to deploy to')
  ])
])

nodejsBuild(${params.TARGETENV}, runtime)