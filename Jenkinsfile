pipeline {
    agent any

    environment {
      VAULT_TOKEN = credentials('vault_token')
      VAULT_ADDR = "https://vaultui.stacklocity.net:8200"
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
