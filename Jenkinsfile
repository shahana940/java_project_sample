pipeline{
    agent{
        label 'node1'
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
        stage('deploy'){
            steps{
                echo "this is deploy stage"
            }
        }
    }
}