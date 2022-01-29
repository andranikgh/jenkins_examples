I have a Jenkins Pipeline using Syntax
It uses a Docker Agent
Chef is installed on that agent
It has to connect to the chef server in the company
And bring the environment values to the Jenkins and store as a json file

Start of code - You can use the below in your Jenkins pipeline. to test


you can start using the following

pipeline {
    stages {
        stage('Get Vault Token') {
            agent {
                label 'windows'
            }
            steps {
                script {
                    VAULT_TOKEN = powershell(returnStdout:true, script: '''
                    $vaultToken = (Invoke-RestMethod -Method Post -Uri "$env:VAULT_URL/v1/auth/userpass/login/$env:VAULT_CRED_USR" -ContentType "application/json" -Body "{`"password`": `"$env:VAULT_CRED_PSW`"}").auth.client_token
                    return $vaultToken
                    ''').trim()
                    assert VAULT_TOKEN != null
                    assert VAULT_TOKEN != ''
                }
            }
            post {
                success {
                    println(' >>>>> SUCCESS: TOKEN Generated!')
                }
                failure {
                    println(' >>>>> FAILURE: TOKEN not generated!')
                }
            }
        }
    }
}