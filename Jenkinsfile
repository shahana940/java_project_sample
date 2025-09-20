pipeline{
    agent{
        label 'node'
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
                echo "this is build step"
                
                
            }
        }
        stage('test'){
            steps{
                echo "this is test stage"
                
             
                
            }
        }

        stage('deploy') {
            steps{
                echo "this is deploy stage"
            }
        }  
       
      
    
       

    }
}
