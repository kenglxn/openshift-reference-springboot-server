#!/usr/bin/env groovy
def config = [
    scriptVersion              : 'v6',
    pipelineScript             : 'https://git.aurora.skead.no/scm/ao/aurora-pipeline-scripts.git',
    downstreamSystemtestJob    : [branch: env.BRANCH_NAME],
    credentialsId              : "github",
    javaVersion                : 11,
    jiraFiksetIKomponentversjon: true,
    chatRoom                   : "#aos-notifications",
    versionStrategy            : [
        [branch: 'master', versionHint: '3'],
        [branch: 'release/v2', versionHint: '2'],
        [branch: 'release/v1', versionHint: '1']
    ]
]
fileLoader.withGit(config.pipelineScript, config.scriptVersion) {
  jenkinsfile = fileLoader.load('templates/leveransepakke')
}
jenkinsfile.run(config.scriptVersion, config)
