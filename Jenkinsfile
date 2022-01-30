pipeline {
    agent any

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }
    stages {
        stage('Get Env of agent)' {
            agent {
                //label 'windows'
                docker {
                    image "chef/chef"
                }
            }
            steps {
                echo "Database engine is ${DB_ENGINE}"
                echo "DISABLE_AUTH is ${DISABLE_AUTH}"
                sh 'printenv'
            }
        }
    }




            /*
            steps {
                //sh "apk add curl"
                sh "echo Hello world"
                script {
                    //VAULT_TOKEN=sh("curl -X GET     --header \"X-Vault-Token: s.uYRC9SO5tvwUitOXkNcdMBOx\"     http://127.0.0.1:8200/v1/sys/mounts ")
                /*    VAULT_TOKEN = powershell(returnStdout:true, script: '''
                    $vaultToken = (Invoke-RestMethod -Method Post -Uri "$env:VAULT_URL/v1/auth/userpass/login/$env:VAULT_CRED_USR" -ContentType "application/json" -Body "{`"password`": `"$env:VAULT_CRED_PSW`"}").auth.client_token
                    return $vaultToken
                    ''').trim()
                    sh "pritnenv"
                    //assert VAULT_TOKEN != null
                    //assert VAULT_TOKEN != ''
                }
            }*/
    post {
        success {
            println(' >>>>> SUCCESS: TOKEN Generated!')
        }
        failure {
            println(' >>>>> FAILURE: TOKEN not generated!')
        }
    }
}