pipeline{
    agent any
    tools {
        terraform  'Terraform'
    }
stages{
    stage('git checkout'){
        steps{
           git credentialsId: 'GirishShetty93', url: 'https://github.com/GirishShetty93/createVMaz.git'
        }
    }
    stage('Terraform init'){
        steps{
            sh 'terraform init'
        }
    }
    stage('Terraform plan'){
        steps{
            sh 'terraform plan'
        }
    }
    stage('Terraform apply'){
        steps{
            sh 'terraform apply -auto-approve'
        }
    }
        
    }
}
