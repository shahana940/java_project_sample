pipeline{
    agent{
        label 'node1'
    }
    tools{
        maven 'maven123'
    }
    parameters {
        string  value:'qwertyyyyy', name:'value'
    }
    stages{
        stage('build'){
            steps{
                sh 'mvn clean package'
                
                
            }
        }
        stage('test'){
            steps{
                echo "this is test stage $params.value"
             
                
            }
        }

        stage('deploy') {
            steps{
                echo "this is deploy stage"
            }
        }  
       
      
    
       

    }
}
