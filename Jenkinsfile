pipeline{
    //Directives
    agent any
    tools {
        maven 'Mavens lab'
    }
    environment{
        ArtifactId = readMavenPom().getArtifactId()
        Version  = readMavenPom().getVersion()
        Name   = readMavenPom().getName()
        GroupId = readMavenPom().getGroupId()
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
                groupId: '${GroupId}', 
                nexusUrl: '192.168.1.7:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'arrydevopslab-SNAPSHOT', 
                version: '${Version}'

            }
        }
        // stage 4 : Print some information
        stage ('publish some information'){
                
            steps {     
               echo "ArtifactsID Is '${ArtifactId}'"
               echo "The Version Is '${Version}'"
               echo "Group Id is '${GroupId}'"
               echo "Name is '${Name}'"

            }
        }
  }
}
