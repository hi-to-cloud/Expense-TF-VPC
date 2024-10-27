pipeline {
    agent {
        label 'hi-to-cloud'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    parameters {
        choice(name: 'Terraform', choices: ['Apply', 'Destroy'], description: 'Pick Action')
    }
    stages {
        stage('PWD') {
            steps {
                sh """ 
                pwd 
                ls -l
                """
            }
        }
        stage('TF Init') {
            when{
                expression{ params.Terraform == 'Apply' }
            }
            steps {
                sh """ 
                terraform init
                """
            }
        }
        stage('TF Plan') {
            when{
                expression{ params.Terraform == 'Apply' }
            }
            steps {
                sh """ 
                terraform plan
                """
            }
        }
        stage('TF Apply') {
            when{
                expression{ params.Terraform == 'Apply' }
            }
            input {
                message "Should we continue?"
                ok "Yes, we should."
            }
            steps {
                sh """ 
                terraform apply -auto-approve
                """
            }
        }
        stage('TF Destroy') {
            when{
                expression{ params.Terraform == 'Destroy' }
            }
            steps {
                sh """ 
                terraform destroy -auto-approve
                """
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        success { 
            echo 'I will run when pipeline is success'
        }
        failure { 
            echo 'I will run when pipeline is failure'
        }
    }
}