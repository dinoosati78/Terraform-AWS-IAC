    pipeline {
        environment {

       AWS_ACCESS_KEY_ID    = credentials('AWS_ACCESS_KEY_ID')

       AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
       
       AWS_DEFAULT_REGION   = "us-east-2"

   }

    agent any

    stages {

    stage('Checkout') {

    steps {

    checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/dinoosati78/Terraform-AWS-IAC.git']]])

    }

    }

    stage ("terraform init") {

    steps {
    dir('lambda')
    {

    sh ('terraform init -no-color')
    }

    }

    }

    stage ('terraform') {

    steps {

    echo "Terraform plan QA"
   
    
   // sh ('cd  C:/Users/Besty/terraform-usecases/Terraform-AWS-IAC/lambda')
     dir('lambda')
    {
    sh ('terraform plan')
    }

    }

    }

    }

    }