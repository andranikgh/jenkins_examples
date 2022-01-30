pipeline {
    agent any
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }
    stages {
        stage('Get Vault Token') {
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