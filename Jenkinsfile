pipeline{
    //Directives
    agent any
    tools {
        maven 'Mavens lab'
    }
    
    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }
        // Stage3 : Publish Artefacts ke Nexus Server
        stage ('Publish to Nexus') {
            steps { 
                script {
                    nexusArtifactUploader artifacts: 
                    [[artifactId: 'ArywsDevOpsLab', 
                    classifier: '', 
                    file: 'target/AryDevOpsLab-0.0.4-SNAPSHOT.war', 
                    type: 'war']], 
                    credentialsId: 'de5f6f6c-87b1-497c-9490-e40cc8e69b60', 
                    groupId: 'com.arywsdevopslab', nexusUrl: '192.168.1.4:8081', 
                    nexusVersion: 'nexus2', protocol: 'http', 
                    repository: 'AryDevOpsLab-SNAPSHOT', version: '0.0.3-SNAPSHOT'
             }
         }
        }
  }
}
