pipeline{
    agent{
        label 'node1'
    }
    tools{
        maven 'maven123'
    }
    parameters {
        string(name: 'value', defaultValue: 'qwertyyyyy', description: 'Enter a value')
        choice choices: ['prod', 'test'], name: 'choice'


    }
    stages{
        stage('build'){
            steps{
                sh 'mvn clean package'
                stash includes:'target/* .war',name
                :'app-artifact'
                
            }
        }
        stage('test'){
            agent{
                label 'node2'
            }
            steps{
                sh 'mkdir unstash'
                dir('unstash/'){
                    unstash 'app-artifact'
             
                }
            }
        }

        stage('deploy') {
            steps{
                echo "this is deploy stage $params.choice"
            }
        }  
       
      
    
       

    }
}
