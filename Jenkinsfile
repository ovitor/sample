pipeline {
    agent any

    triggers {
      pollSCM('*/5 * * * *')
    }

    environment {
      VAULT_TOKEN = credentials('vault_token')
      VAULT_ADDR = "https://vault-1.hvvc.local:8200"
    }

    stages {
        stage('pre-build') {
            steps {
                echo 'this is the pre build stage'
                sh 'terraform-0.12 version'
                sh 'vault version'
                sh 'vault kv get secret/sample'
            }
        }
    }
}
