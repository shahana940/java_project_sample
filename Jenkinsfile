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
                echo "this is build"
                }
                
            }
        }
        stage('test'){
            agent{
                label "node2"
            }
            when{expression{params.servers=="prod"}}
            steps{
                timeout(time:5,unit:'DAYS'){
                        input message:"approve deployment in production server"
                        echo 'this is test'
                        sh "mkdir unstash"
                        dir("unstash"){
                            unstash "build"
                        }
                }
             
                
            }
        }

   
       
      
    
       

    }
}
