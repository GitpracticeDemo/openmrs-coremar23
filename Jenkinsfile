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
            steps {
                bat label: 'My batch script',
                    script: ''' @echo off
                                return_1_if_success.exe   // command which returns 1 in case of success, 0 otherwise
                                IF %ERRORLEVEL% EQU 1 (exit /B 0) ELSE (exit /B 1)'''
            }
          stage('post build') {
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