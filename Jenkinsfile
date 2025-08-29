pipeline{
    agent{
        label 'node1'
    }
    tools{
        maven 'maven123'
    }
    parameters {
        choice choices: ['prod', 'dev'], name: 'servers'
    }
    options{
        skipDefaultCheckout(true)
    }
    stages{
        stage('build'){
            steps{
                checkout scm
                echo "this is $params.value"
                sh "mvn clean package"
            }
        }
        stage('test'){
            steps{
                echo 'this is test'
            }
        }
       
      
    
       

    }
}
