pipeline{
    
    agent any
    
    stages{
        
        stage('Checkout source code'){
            steps{
                git 'https://github.com/gabrielf/maven-samples.git'
            }
        }
        
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        
        stage('Archival'){
            steps{
                archiveArtifacts 'multi-module/webapp/target/*.war'
            }
        }
        
        stage('Publish artifacts to S3'){
            steps{
                s3Upload consoleLogLevel: 'INFO', dontWaitForConcurrentBuildCompletion: false, entries: [[bucket: 'jenkins-artifacts-rajesh', excludedFile: '', flatten: false, gzipFiles: false, keepForever: false, managedArtifacts: false, noUploadOnFailure: false, selectedRegion: 'us-east-1', showDirectlyInBrowser: false, sourceFile: 'multi-module/webapp/target/*.war', storageClass: 'STANDARD', uploadFromSlave: false, useServerSideEncryption: false]], pluginFailureResultConstraint: 'FAILURE', profileName: 'jenkins', userMetadata: []

            }
        }
    }
    
}
