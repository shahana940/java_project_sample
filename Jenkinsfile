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

                stash name:"build",includes:"target/*.war"
            }
        }
        stage('test'){
            agent{
                label "node2"
            }
            steps{
                echo 'this is test'
                unstash "build"
            }
        }

        stage("hello")[
            
        ]
       
      
    
       

    }
}
