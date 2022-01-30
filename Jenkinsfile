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
                #sh "apk add curl"
                sh "echo Hello world"
                script {
                    //VAULT_TOKEN=sh("curl -X GET     --header \"X-Vault-Token: s.uYRC9SO5tvwUitOXkNcdMBOx\"     http://127.0.0.1:8200/v1/sys/mounts ")
                /*    VAULT_TOKEN = powershell(returnStdout:true, script: '''
                    $vaultToken = (Invoke-RestMethod -Method Post -Uri "$env:VAULT_URL/v1/auth/userpass/login/$env:VAULT_CRED_USR" -ContentType "application/json" -Body "{`"password`": `"$env:VAULT_CRED_PSW`"}").auth.client_token
                    return $vaultToken
                    ''').trim()*/
                    ENV=$(sh "pritnenv")
                    echo $ENV > a.json
                    //assert VAULT_TOKEN != null
                    //assert VAULT_TOKEN != ''
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