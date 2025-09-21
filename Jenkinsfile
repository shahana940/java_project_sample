pipeline{
    agent{
        label 'node1'
    }
    tools{
        maven 'maven123'
    }
    parameters {
        string(name: 'value', defaultValue: 'qwertyyyyy', description: 'Enter a value')
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
                stash includes:'target/*.war',name:'app-artifact'
                
            }
        }
        stage('test'){
            agent{
                label 'node2'
            }
            steps{
                sh 'rm -rf unstash &&mkdir unstash'
                dir('unstash/'){
                    unstash 'app-artifact'
             
                }
                echo "this is test stage $params.value"
            }
        }

        stage('deploy') {
            steps{
                echo "this is deploy stage $params.choice"
            }
        }  
       
      
        stage('parallel'){
            parallel{
                stage('testA'){
                    steps{
                        echo 'test A parallel'
                    }
                }
                stage('testB'){
                    steps{
                        echo 'test A parallel'
                    }
                }
                stage('testc'){
                    steps{
                        echo 'test A parallel'
                    }
                }
            }
        }
       

    }
}
