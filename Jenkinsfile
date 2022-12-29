pipeline{
    agent any
    tools {
        terraform  'Terraform'
    }
environment {
    ARM_CLIENT_ID = "1b1ba36d-db66-436a-aebb-8bd0085a331c"
    ARM_CLIENT_SECRET = "-tu8Q~wl3d1EfJ.r08Ft4W3GS3SV7_1mo5gJ6dy8"
    ARM_TENANT_ID = "7453a23a-f546-4af3-8d42-5b4505f1049a"
    ARM_SUBSCRIPTION_ID= "7de549ce-97a6-4181-a393-0a86e3c9525c"
}
stages{
    stage('git checkout'){
        steps{
           git credentialsId: 'GirishShetty93', url: 'https://github.com/GirishShetty93/createVMaz.git'
        }
    }
    stage("Azure Terraform Login") {
	steps {
	   sh "az login --service-principal -u $ARM_CLIENT_ID -p $ARM_CLIENT_SECRET --tenant $ARM_TENANT_ID"
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
