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
        },
            creadentialsid: 'nexus3',
            groupid: 'in.javahome',
            nexusversion: 'nexus3',
            protocol: 'http',
            repository: '',
            version:'1.0.0'
            
      
            }
        }
    }
}

