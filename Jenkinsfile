pipeline {
    agent {
        label 'hi-to-cloud'
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
            steps {
                sh """ 
                terraform init
                """
            }
        }
        stage('TF Plan') {
            steps {
                sh """ 
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