pipeline{
      agents { label '' }
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