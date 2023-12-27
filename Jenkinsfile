@Library("jenkins-shared-libs@main") _

properties([
  parameters([
        choice(name: 'TARGETENV', choices: ['DEV','SIT','UAT','PROD'], description: 'Target environment to deploy to'),
        choice(name: 'AWSREGION', choices: ['eu-west-1'],description: 'Target region to deploy to'),
        string(name: 'IMAGE_TO_DEPLOY', defaultValue: '', description: 'This param is used for UAT and PROD deploys. No new image is built, instead an image previously built and deployed to SIT is used. Enter the desired image name to deploy (image name is printed after the git hash in the build history. For SIT and DEV this parameter is ignored.')

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
  appName: 'testapp',
  appType: 'nodejs',
  helmChartRepoBaseURL: "https://github.com/razeen-bahadoor",
  helmChartRepo: "node-docker-demo",
  helmChartValues : "live/${params.TARGETENV.toString().toLowerCase()}/${this.appName}",
  imageToDeploy: params.IMAGE_TO_DEPLOY
)
)