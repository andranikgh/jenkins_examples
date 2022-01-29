pipeline {
    agent any
    stages {
        stage('Get Vault Token') {
            agent {
                //label 'windows'
                docker {
                    image "chef/chef"
                }
            }
            steps {
                sh "echo Hello world"
                script {
                    VAULT_TOKEN="HELLO"
                /*    VAULT_TOKEN = powershell(returnStdout:true, script: '''
                    $vaultToken = (Invoke-RestMethod -Method Post -Uri "$env:VAULT_URL/v1/auth/userpass/login/$env:VAULT_CRED_USR" -ContentType "application/json" -Body "{`"password`": `"$env:VAULT_CRED_PSW`"}").auth.client_token
                    return $vaultToken
                    ''').trim()*/
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