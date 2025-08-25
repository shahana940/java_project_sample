pipeline{
    agent {
        label "node1"
    }
    tools{
        maven "maven123"
    }
    stages{
       stage('build'){
        steps{
            echo "this is build stage"
            sh "mvn package"
        }
        
       }
       stage("test"){
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