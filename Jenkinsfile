pipeline {
    agent {
        label 'hi-to-cloud'
    }
    stages {
        stage('TF Init') {
            steps {
                sh """ 
                cd Expense-TF-VPC
                terraform init
                """
            }
        }
        stage('TF Plan') {
            steps {
                sh """ 
                cd Expense-TF-VPC
                terraform plan
                """
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo This is Deploy'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        success { 
            echo 'I will run when pipeline is success'
        }
        failure { 
            echo 'I will run when pipeline is failure'
        }
    }
}