pipeline {
    agent any
    tools {
        maven 'maven3'
    }
   
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
            }
          }
        
        stage ('upload war to nexus'){
            steps{
                nexusartfactuploader aretifacts:
                    [
                        artifactid: 'simple-app',
                        classifier: '',
                        file: 'target/sample-app-1.0.0.war',
                        type: 'war',
                     ]
        }
            creadentialsid: 'nexus2',
            groupid: 'in.javahome',
            nexusurl: '3.87.184.249:8081',
            nexusversion: 'nexus2',
            protocol: 'http',
            repository: 'simpleapp-release',
            version:'1.0.0'
            
      
            }
        }
    }
}

