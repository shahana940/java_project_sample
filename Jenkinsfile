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
    options{
        skipDefaultCheckout(true)
    }

    stages{
        stage('build'){
            steps{
                checkout scm
                sh 'mvn clean package'
                stash includes: 'target/*.war',name:'app_artifact'
            }
        }

        stage('test'){
            agent{
                label 'node2'
            }
            steps{
                sh 'rm -rf unstash && mkdir unstash'
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
        stage('parallel'){
            parallel{
                stage('test A'){
                    steps{
                        echo 'test A parallel'
                    }
                }
                stage('test B'){
                    steps{
                        echo 'test A parallel'
                    }
                }
                stage('test C'){
                    steps{
                        echo 'test A parallel'
                    }
                }              

            }
        }
    }
}


