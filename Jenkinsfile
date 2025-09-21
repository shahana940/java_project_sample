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
            when{
                expression{
                    params.choice == 'prod'}}

            agent{
                label 'node2'
             }
            steps{
                echo "this is deploy stage $params.choice"
                sh 'rm -rf unstash & mkdir unsttash'
                dir('unstash'){
                    unstash 'app_artifact'
                }
                timeout(time:5,unit:'DAYS')
                input message:'approve deployment in production'
                sh "echo hello> deployment"
            }
        }

    }
}
