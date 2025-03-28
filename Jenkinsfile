pipeline{
    agent {
        label "node1"
    }
    parameters {
        string defaultValue: 'production', name: 'server'
    }
    stages{
        stage("build"){
            steps{
                echo "this is build block $params.server"
            }
            
        }

        stage("test"){
            steps{
                echo "this is test block"
            }
            
        }

        stage("deploy"){
            steps{
                echo "this is deploy block"
            }
            
        }
    }
}