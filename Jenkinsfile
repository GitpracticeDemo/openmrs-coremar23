pipeline {
      agent { label 'SPRING-PET' }
      stages {
          stage('vcs') {
            steps {
                git url: 'https://github.com/GitpracticeDemo/openmrs-coremar23.git',
                    branch: 'declarative'
            }
          }  
          stage('package') {
            steps {
                  sh 'export "PATH=/usr/lib/jvm/java-1.8.0-openjdk-amd64:$PATH"',
                  sh 'mvn package'
            }
          }
          stage('build') {
            steps {
                archiveArtifacts artifacts: '**/openmrs-liquibase-2.7.0-SNAPCHAT-tests.jar',
                                 allowEmptyArchive: true,
                                 onlyIfSuccessful: true,
                                 fingerprint: true
                                 junit testResults: '**/surefire-reports/TEST-*.xml'   
            }
          }    
      }
      
}