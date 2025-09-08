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
                dir('target'){
                    stash name:"build",includes:"*.war"
                }
                
            }
        }
        stage('test'){
            agent{
                label "node2"
            }
            when{expression{params.servers=="prod"}}
            steps{
                echo 'this is test'
                sh "mkdir unstash"
                dir("unstash"){
                    unstash "build"
                }
                
            }
        }

   
       
      
    
       

    }
}
