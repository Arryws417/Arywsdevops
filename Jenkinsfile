pipeline{
    //Directives
    agent any
    tools {
        maven 'Mavens lab'
    }
    environment{
        artifactId = readMavenPom().getArtifactId()
        version  = readMavenPom().getVersion()
        name   = readMavenPom().getName()
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
            steps { nexusArtifactUploader artifacts: [[
                artifactId: 'ArywsDevOpsLab', 
                classifier: '', 
                file: 'target/ArywsDevOpsLab-0.0.4-SNAPSHOT.war', 
                type: 'war']], 
                credentialsId: '7af5b573-7d08-4725-899c-22e2bed1714e', 
                groupId: 'com.arywsdevopslab', 
                nexusUrl: '192.168.1.7:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'arrydevopslab-SNAPSHOT', 
                version: '0.0.4-SNAPSHOT'

            }
        }
        }
}
