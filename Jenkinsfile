#!/usr/bin/env groovy

@Library('dais-lib@dais-pipeline') _

properties([
        pipelineTriggers([cron('00 13 * * *')]), // Every day at 8 AM
])

pipelineWrapper(true, 2) {
    stage('Cleanup') {
        env.alertChannels = "automation-team"
        def result = sh script: 'curl http://zalenium.service.dev.dais.com/dashboard/cleanup?action=doCleanup', returnStdout: true
        if (result != 'SUCCESS') {
            slack('FAILED')
        }
        assert result == 'SUCCESS'
    }
}
