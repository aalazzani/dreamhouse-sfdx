#!groovy

import groovy.json.JsonSlurperClassic

node {

    def SF_CONSUMER_KEY=env.SF_CONSUMER_KEY
    def SF_USERNAME=env.SF_USERNAME
    def SERVER_KEY_CREDENTALS_ID=env.SERVER_KEY_CREDENTALS_ID
    def TEST_LEVEL='RunLocalTests'
    def PACKAGE_NAME='0Ho1U000000CaUzSAK'
    def PACKAGE_VERSION
    def SF_INSTANCE_URL = env.SF_INSTANCE_URL ?: "https://login.salesforce.com"
    //def JWT = "MIIEpAIBAAKCAQEAwi46giRxhdnBWsTg6XD5AzHMCtmIeb08CUje9BuoUzxjO1RXjS4BLubCAsdNKn3t8lXKjD/cXukDpJZQckywcNixVHPK9Ilh/loXuOM+3hRMvoXazoO/ccGA7rIDZnPKY1R3YZ2G3bwqgYa+jWqjjanJvymHQDp0jeKCOm1r5k+521w5CLKSfU2PGvByXzUldoafeyEFokgSsu3xJ2oO1cBqVEDQCV26n5E3AL6Okc1q1mDOKVcD09ZPMEe+xQmu0pwyxwQAJRTxJTq53gtwv7qjhDYFqZ+JkDFtNR9zb4mVghpvkBZxnefQBrF6Lh8oJdt0AV+TLr/fMIOe5D0HZQIDAQABAoIBAQCqKca9+1+8U0nc2EDccVLWGNJdA6pUPJ+a50/yDTah0n6HJG8g2hrRVgjYVHzr6rUVM1cvNltQlNPLbKoMr+XCzjH/9wT47FeChMLbE9Eo3hMutrA7XzrqXg81navbIUdPalq/oULplxaMsV7VIIk5AHw6WBMdFtzC5acHupHenZ/kARmdGnNQmz9jIZYGvYUA9cepTs04BdbZ9SNVkC2InuX+2U+5e4GNknG3ZA1ad0cuuF3U8gZFVcYEnoa9RvBiWlmN35QWrd9OnqkEJLcHqqkoBXy4I3S2aDnEPF08kIa9CV3NZl90bQoiZsq/7w9KNXAO9H+/JKz7voadZiwVAoGBAPlUidJZRC7ZifJsL5wudVmqq2ehBKxKPL3jPlOsrQR9pmhycy6WavYEYh30nszqf7ZqM8EXoCmElYuuVzdGHYJzVX7pBy41s9tkj5wddX4kzD24GG1RcfCEH+QiCelg407xj/sgHEEIyih1XVPeLVLP5VoyyAOZgmWZZCrHGsfLAoGBAMdgA8UXGp8gBiLaNbQMfmV9VEAiOPR9IW6oKme9qnYFXjfT/zaty6YLiS27IueUjWinUgYUEqwdWvM4GkyTvr1DPVMLVnu5tflejvkZVO3yBO0/3sIwWpRRfYAWDD0hLjTaNJTUzkHPzAM1O26YwTNlsXHhpmEGlq7MQ2AJlqePAoGAWPVvwyx0Zl7ZmDQ/fHMbDaYWSAAsYaiPKZUlzMcEaGDIeeWz8QBcI3EG7Pc1nZlhfd1An/lk/MtAbDkFB0SuDLhH3eMY28TvaizkDGh6XkqU0MSZeo+fnpgVpNj8PleCYs1PeONJEW8oae0OInlYJH7mrxsFQDuKSePD2Ht3s6cCgYAb8T/2Amvvu0xA3DZEmq+oR61kI6e51EO4P4dZ7MIUMmJnDqYpIqh1CA7cwup8bFx5O2IKigun5aFWjxlYfChyXBcfKWqggoGXhoIhNUSq6I16NsZgjuhS+yzMo8ppUton/CD8burNXHMqS+6dbHk/W9RHsqlf1c2OiAA1WIKtzwKBgQDF3YZ+kbSU1c9SZITvYDszJxEgIfW5ECxnsNCsAdWHF/lhJsL90FaKD7D52VbqPmbTEnzEgFSRfteaAz6cuyHJD2b03DjDndpGXbw0rvvcEBDY3ZSXjdykfr/4v8ljHs2xqafakxBjEkzyUpfi+Q+znieX8FNK0TXZ1Pq3J7HMlA=="
    //def JWT = "/Users/aalazzani/Desktop/myWorkspace/certs/server.key"
    
    def toolbelt = tool 'toolbelt'

    

    // -------------------------------------------------------------------------
    // Check out code from source control.
    // -------------------------------------------------------------------------

    stage('checkout source') {
        checkout scm
    }


    // -------------------------------------------------------------------------
    // Run all the enclosed stages with access to the Salesforce
    // JWT key credentials.
    // -------------------------------------------------------------------------
    
    withEnv(["HOME=${env.WORKSPACE}"]) {
        
        
        withCredentials([file(credentialsId: SERVER_KEY_CREDENTALS_ID, variable: 'server_key_file')]) {

            // -------------------------------------------------------------------------
            // Authorize the Dev Hub org with JWT key and give it an alias.
            // -------------------------------------------------------------------------

            stage('Authorize DevHub') {
                //rc = command "${toolbelt}/sfdx force:auth:jwt:grant --instanceurl ${SF_INSTANCE_URL} --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${server_key_file} --setdefaultdevhubusername --setalias HubOrg"
                //rc = command "${toolbelt}/sfdx force:auth:jwt:grant --instanceurl ${SF_INSTANCE_URL} --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${JWT} --setdefaultdevhubusername --setalias HubOrg"
                //rc = command "${toolbelt}/sfdx force:auth:jwt:grant --instanceurl https://login.salesforce.com --clientid 3MVG9xB_D1giir9qLlIIq9fZmbqhlRDBbkdFYQLRotyxrPX56rH8pyIY0Oudba4fZNO6zoO5m1Q4udNQJnOl6 --username aalazzani@sfdx.com --jwtkeyfile '/Users/aalazzani/Desktop/myWorkspace/certs/server.key' --setdefaultdevhubusername --setalias HubOrg"
                
                SFDX_OUTPUT = sh (
                    script: '${toolbelt}/sfdx force:auth:jwt:grant --instanceurl ${SF_INSTANCE_URL} --clientid ${SF_CONSUMER_KEY} --username ${SF_USERNAME} --jwtkeyfile ${server_key_file} --setdefaultdevhubusername --setalias HubOrg',
                    returnStdout: true
                ).trim()
                print "SFDX_OUTPUT is ${SFDX_OUTPUT}"
                
                rc = 1
                
                if (rc != 0) {
                    error 'Salesforce dev hub org authorization failed.'
                }
                
                
            }


            // -------------------------------------------------------------------------
            // Create new scratch org to test your code.
            // -------------------------------------------------------------------------

            stage('Create Test Scratch Org') {
                rc = command "${toolbelt}/sfdx force:org:create --targetdevhubusername HubOrg --setdefaultusername --definitionfile config/project-scratch-def.json --setalias ciorg --wait 10 --durationdays 1"
                if (rc != 0) {
                    error 'Salesforce test scratch org creation failed.'
                }
            }


            // -------------------------------------------------------------------------
            // Display test scratch org info.
            // -------------------------------------------------------------------------

            stage('Display Test Scratch Org') {
                rc = command "${toolbelt}/sfdx force:org:display --targetusername ciorg"
                if (rc != 0) {
                    error 'Salesforce test scratch org display failed.'
                }
            }


            // -------------------------------------------------------------------------
            // Push source to test scratch org.
            // -------------------------------------------------------------------------

            stage('Push To Test Scratch Org') {
                rc = command "${toolbelt}/sfdx force:source:push --targetusername ciorg"
                if (rc != 0) {
                    error 'Salesforce push to test scratch org failed.'
                }
            }


            // -------------------------------------------------------------------------
            // Run unit tests in test scratch org.
            // -------------------------------------------------------------------------

            stage('Run Tests In Test Scratch Org') {
                rc = command "${toolbelt}/sfdx force:apex:test:run --targetusername ciorg --wait 10 --resultformat tap --codecoverage --testlevel ${TEST_LEVEL}"
                if (rc != 0) {
                    error 'Salesforce unit test run in test scratch org failed.'
                }
            }


            // -------------------------------------------------------------------------
            // Delete test scratch org.
            // -------------------------------------------------------------------------

            stage('Delete Test Scratch Org') {
                rc = command "${toolbelt}/sfdx force:org:delete --targetusername ciorg --noprompt"
                if (rc != 0) {
                    error 'Salesforce test scratch org deletion failed.'
                }
            }


            // -------------------------------------------------------------------------
            // Create package version.
            // -------------------------------------------------------------------------

            stage('Create Package Version') {
                if (isUnix()) {
                    output = sh returnStdout: true, script: "${toolbelt}/sfdx force:package:version:create --package ${PACKAGE_NAME} --installationkeybypass --wait 10 --json --targetdevhubusername HubOrg"
                } else {
                    output = bat(returnStdout: true, script: "${toolbelt}/sfdx force:package:version:create --package ${PACKAGE_NAME} --installationkeybypass --wait 10 --json --targetdevhubusername HubOrg").trim()
                    output = output.readLines().drop(1).join(" ")
                }

                // Wait 5 minutes for package replication.
                sleep 300

                def jsonSlurper = new JsonSlurperClassic()
                def response = jsonSlurper.parseText(output)

                PACKAGE_VERSION = response.result.SubscriberPackageVersionId

                response = null

                echo ${PACKAGE_VERSION}
            }


            // -------------------------------------------------------------------------
            // Create new scratch org to install package to.
            // -------------------------------------------------------------------------

            stage('Create Package Install Scratch Org') {
                rc = command "${toolbelt}/sfdx force:org:create --targetdevhubusername HubOrg --setdefaultusername --definitionfile config/project-scratch-def.json --setalias installorg --wait 10 --durationdays 1"
                if (rc != 0) {
                    error 'Salesforce package install scratch org creation failed.'
                }
            }


            // -------------------------------------------------------------------------
            // Display install scratch org info.
            // -------------------------------------------------------------------------

            stage('Display Install Scratch Org') {
                rc = command "${toolbelt}/sfdx force:org:display --targetusername installorg"
                if (rc != 0) {
                    error 'Salesforce install scratch org display failed.'
                }
            }


            // -------------------------------------------------------------------------
            // Install package in scratch org.
            // -------------------------------------------------------------------------

            stage('Install Package In Scratch Org') {
                rc = command "${toolbelt}/sfdx force:package:install --package ${PACKAGE_VERSION} --targetusername installorg --wait 10"
                if (rc != 0) {
                    error 'Salesforce package install failed.'
                }
            }


            // -------------------------------------------------------------------------
            // Run unit tests in package install scratch org.
            // -------------------------------------------------------------------------

            stage('Run Tests In Package Install Scratch Org') {
                rc = command "${toolbelt}/sfdx force:apex:test:run --targetusername installorg --resultformat tap --codecoverage --testlevel ${TEST_LEVEL} --wait 10"
                if (rc != 0) {
                    error 'Salesforce unit test run in pacakge install scratch org failed.'
                }
            }


            // -------------------------------------------------------------------------
            // Delete package install scratch org.
            // -------------------------------------------------------------------------

            stage('Delete Package Install Scratch Org') {
                rc = command "${toolbelt}/sfdx force:org:delete --targetusername installorg --noprompt"
                if (rc != 0) {
                    error 'Salesforce package install scratch org deletion failed.'
                }
            }
        }
    }
}

def command(script) {
    if (isUnix()) {
        return sh(returnStatus: true, script: script);
    } else {
        return bat(returnStatus: true, script: script);
    }
}
