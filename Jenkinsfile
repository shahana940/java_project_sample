pipeline{
    agent{
        label "node1"
    }

    environment{
        deploy_dir = "/opt/tomcat/myapp_dir"
    }

    tools{
        maven "maven"
    }

    stages{
        stage('git checkout'){
            steps{
                git branch: 'main',url: 'https://github.com/AmalkumarG/java_proj_sample.git'
            }
            
        }

        stage('build app'){
            steps{
                echo "build stage on exec"
                sh 'mvn clean package'
            }
        }

        stage('deploy to tomcat'){
            steps{
                echo "deploy stage running"
                //clean old files
                sh "sudo rm -rf $deploy_dir/*"

                sh "sudo unzip -o target/java-tomcat-maven-example.war -d $deploy_dir"

                sh "sudo chown -R tomcat:tomcat $deploy_dir"
                
            }
        }

        stage("restart tomcat"){
            steps{
                sh "sudo systemctl restart tomcat"
            }
        }
    }
}