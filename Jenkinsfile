#!groovy

//noinspection GroovyAssignabilityCheck
properties(
        [[$class: 'GithubProjectProperty', displayName: 'Cross browser E2E tests', projectUrlStr: 'https://github.com/hmcts/cmc-cross-browser-e2e'],
         pipelineTriggers([
                 [$class: 'GitHubPushTrigger']
         ])]
)

timestamps {
    node {
        stage('Checkout') {
            deleteDir()
            checkout scm
        }

        stage('Dummy') {
            sh 'echo Hello, World!'
        }
    }
}

