#!groovy

//noinspection GroovyAssignabilityCheck
properties(
        [[$class: 'GithubProjectProperty', displayName: 'Cross browser E2E tests', projectUrlStr: 'https://github.com/hmcts/cmc-cross-browser-e2e'],
         pipelineTriggers([
                 [$class: 'GitHubPushTrigger'],
                 [$class: 'hudson.triggers.TimerTrigger', spec  : 'H 3 * * *']
         ])]
)

@Library(['Reform', 'CMC'])
import uk.gov.hmcts.cmc.integrationtests.IntegrationTests

IntegrationTests integrationTests = new IntegrationTests(env, this, "docker-compose.cross-browser.yml")

timestamps {
    node {
        stage('Checkout') {
            deleteDir()
            checkout scm
        }

        stage('Run cross browser tests') {
            env.INTEGRATION_TESTS_BRANCH = 'master'
            integrationTests.executeCrossBrowser([
                'INTEGRATION_TESTS_VERSION': 'latest'
            ])
        }
    }
}
