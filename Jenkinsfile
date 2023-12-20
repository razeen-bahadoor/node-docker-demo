@Library("jenkins-shared-libs@main") _

properties([
  parameters([
        choice(name: 'TARGETENV', choices: ['AUTO','DEV','SIT','UAT','PROD'], description: 'Target environment to deploy to')
  ])
])

nodejsPipeline(params.TARGETENV,"testapp")