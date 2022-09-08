pipeline { 
    agent any  
    stages { 

        stage('Source Code') { 
            steps { 
                sh '''
                rm -rf java-hello-world-webapp-scripted
               git clone https://github.com/sarathkrishna2018/java-hello-world-scripted.git
               '''
            }
        }

        stage('Build') { 
            steps { 
               echo 'this is build stage' 
               sh '''
               ls
               pwd
               mvn clean install
               '''
            }
        }

        stage('Deploy to Tomcat') { 
            steps { 
                deploy adapters: [tomcat7(credentialsId: 'jenkins-tomcat-manager', path: '', url: 'http://3.83.239.14:8080/')], contextPath: 'hello-world-scripted1', war: '**/*.war' 
            }
        }
    }
}
