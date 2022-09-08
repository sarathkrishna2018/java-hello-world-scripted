pipeline { 
    agent any  
    stages { 

        stage('Source Code') { 
            steps { 
                sh '''
                rm -rf java-hello-world-webapp
               git clone https://github.com/sarathkrishna2018/java-hello-world-webapp.git
               '''
            }
        }

        stage('Build') { 
            steps { 
               echo 'this is build stage' 
               sh '''
               cd java-hello-world-webapp
               mvn clean install
               '''
            }
        }

        stage('Deploy to Tomcat') { 
            steps { 
                deploy adapters: [tomcat7(credentialsId: 'jenkins-tomcat-manager', path: '', url: 'http://3.83.239.14:8080/')], contextPath: 'hello-world', war: '**/*.war' 
            }
        }
    }
}
