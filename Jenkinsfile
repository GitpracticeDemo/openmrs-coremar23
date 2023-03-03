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
                    sh 'export "PATH=/usr/lib/jvm/java-1.8.0-openjdk-amd64:$PATH" && mvn package'     
            }
          }
          stage('build') {
            steps {
                  archiveArtifacts artifacts: '**/*.txt',
                                   allowEmptyArchive: true,
                                   fingerprint: true,
                                   onlyIfSuccessful: true
                                   junit testResults: '**/surefire-reports/TEST-*.xml'   
            }
          }    
      }
      
}