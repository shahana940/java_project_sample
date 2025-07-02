pipeline{
    agent{
        label 'node1'
    }
    tools{
        maven 'maven123'
    }
    parameters {
        string defaultValue: 'qwertyyyyyy', name: 'value'
        choice choices: ['prod', 'test'], name: 'choice'
    }

    stages{
        stage('build'){
            steps{
                sh 'mvn clean package'
                stash includes: 'target/*.war',name:'app_artifact'
            }
        }

        stage('test'){
            agent{
                label 'node2'
            }
            steps{
                sh 'mkdir unstash'
                dir('unstash/'){
                    unstash 'app_artifact'

                }
                echo "this is test stage $params.value"
                 
            }
        }
        stage('deploy'){
            steps{
                echo "this is deploy stage $params.choice"
            }
        }
    }
}


