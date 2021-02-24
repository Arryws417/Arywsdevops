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
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab'
                classifier: '', 
                file: 'target/arrydevopslab-0.0.4-SNAPSHOT.war'
                type: 'war']],
                credentialsId: '417',
                groupId: 'com.vinaysdevopslab',
                nexusUrl: '192.168.1.7:8081',
                nexusVersion: 'nexus3',
                protocol: 'http',
                repository: 'arrydevopslab-SNAPSHOT',
                version: '0.0.4-SNAPSHOT'
            }
        }
        // Stage4 : Print some information
        stage ('Print environment variables') {
          steps {
              echo "Artifact ID is '${artifactId}'"
              echo "Version is '${version}'"
              echo "GroupID is '{}'"
              echo "Name is '${name}'"
          }
        }
    }
}
