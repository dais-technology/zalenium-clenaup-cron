#!/usr/bin/env groovy

@Library('dais-lib@dais-pipeline') _

properties([
        pipelineTriggers([cron('00 13 * * *')]), // Every day at 8 AM
])

env.alertChannels = "automation-team"

pipelineWrapper(true, 30) {
    def result = sh script: 'curl http://zalenium.service.dev.dais.com/dashboard/cleanup?action=doCleanup', returnStdout: true
    assert result == 'SUCCESS'
}
