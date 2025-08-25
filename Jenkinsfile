pipeline{
    agent {
        label "node1"
    }
    tools{
        maven "maven123"
    }
    options{
        skipDefaultCheckout(true)
    }
    parameters {
        string defaultValue: 'dev', name: 'server'
    }

    stages{
       stage('build'){
        steps{
            checkout scm
            echo "this is build stage $params.server"
            sh "mvn package"
        }
        
       }
       stage("test"){
        agent{
            label "node2"
        }
        steps{
            echo "this is test stage"
        }
        
       } 
       stage("deploy"){
            parallel{
               stage('testA'){
                steps{
                    echo "TESTA"
                }
               } 
                stage('testB'){
                    steps{
                        echo "TESTB"
                    }
                }
            }
        
       }
    }
}