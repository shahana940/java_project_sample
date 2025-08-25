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
    stages{
       stage('build'){
        steps{
            checkout scm
            echo "this is build stage"
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
        steps{
            echo "this is deploy stage"
        }
        
       }
    }
}