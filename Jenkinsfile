@Library("jenkins-shared-libs@main") _

properties([
  parameters([
        choice(name: 'TARGETENV', choices: ['DEV','SIT','UAT','PROD'], description: 'Target environment to deploy to'),
        choice(name: 'AWSREGION', choices: ['eu-west-1'],description: 'Target region to deploy to')
  ])
])

nodejsPipeline(new BuildConfig(
  awsAccountIds : [
            'DEV': 'xyz',
            'SIT': 'xyz',
            'UAT': 'xyz',
            'PROD': 'xyz'
  ],
  awsRegion: params.AWSREGION,
  env : params.TARGETENV,
  awsCrossAccountDeploymentRole: 'Bounded-jenkins-crossaccount-deployment-role',
  appName: 'testapp'
  appType: 'nodejs'
)
)