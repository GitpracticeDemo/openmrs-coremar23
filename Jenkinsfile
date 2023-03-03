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
                  sh 'mvn package'
            }
          }
          stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/*.txt',
                                 allowEmptyArchive: true,
                                 onlyIfSuccessful: true,
                                 fingerprint: true
                                 junit testResults: '**/surefire-reports/TEST-*.xml'   
            }
          }    
      }
      
}