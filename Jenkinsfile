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
                
                echo "this is test stage $params.value"
                 
            }
        }
        stage('deploy'){
            when{expression{params.choice=='prod'}}
            agent{
                label 'node2'
            }
            steps{
                echo "this is deploy stage $params.choice"
                sh 'rm -rf unstash && mkdir unstash'
                dir('unstash/'){
                    unstash 'app_artifact'
                }
                timeout(time:5,unit:'DAYS'){
                    input message:'approve deployment in production'
                    sh "echo hello > deployment"
                    sh "docker stop tomcat||true&&docker rm tomcat||true"
                    sh "docker run -d --name tomcat -p 80:8080 tomcat"
                    sh "docker cp unstash/target/*.war tomcat:/usr/local/tomcat/webapps"
                    
                }

                
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


