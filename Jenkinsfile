pipeline {
    agent any
    tools {
        maven 'maven3'
    }
   
    stages{
        stage('Build'){
            steps{
                 sh script: 'mvn clean package'
                 archiveArtifacts artifacts: 'target/*.war', 
        }
            
        stage('Upload War To Nexus'){
            steps{
                script{

                        [
                            artifactId: 'simple-app', 
                            classifier: '', 
                            file: 'target/simple-app-1.0.0.war', 
                            type: 'war'
                    ], 
                            
                    credentialsId: 'nexus3', 
                    groupId: 'in.javahome', 
                    nexusUrl: '54.211.11.250:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository:'simpleapp-release', 
                    version: "1.0.0"
                    }
            }
        }
    }
}

