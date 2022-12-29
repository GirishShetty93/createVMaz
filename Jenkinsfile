pipeline{
    agent any
    tools {
        terraform  'Terraform'
    }
environment {
    ARM_CLIENT_ID="f103ca34-623c-414f-837d-4815230f9592"
    ARM_CLIENT_SECRET="bc5180b2-167d-4d5a-8898-1e02126040a3"
    ARM_SUBSCRIPTION_ID="7de549ce-97a6-4181-a393-0a86e3c9525c"
    ARM_TENANT_ID="7453a23a-f546-4af3-8d42-5b4505f1049a"
}
stages{
    stage('git checkout'){
        steps{
           git credentialsId: 'GirishShetty93', url: 'https://github.com/GirishShetty93/createVMaz.git'
        }
    }
    stage("Azure Terraform Login") {
	steps {
	   sh "az login --service-principal --username $ARM_CLIENT_ID --password $ARM_CLIENT_SECRET --tenant $ARM_TENANT_ID"
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
