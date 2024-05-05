pipeline {
    agent any
    stages {
        stage('Test Connection') {
            steps {
                // Checkout the repository without checking out any files
                checkout([$class: 'GitSCM', 
                          branches: [[name: '*/develop']], 
                          doGenerateSubmoduleConfigurations: false, 
                          extensions: [[$class: 'DisableRemotePoll']], 
                          submoduleCfg: [], 
                          userRemoteConfigs: [[url: 'https://github.com/Atala66/JENKINS_CASO_1.git']]])
                
                // Print a message indicating successful connection
                echo 'Connection test successful'
            }
        }
        stage('Build') {
            steps {
                echo 'En Python no hay etapa build'
                echo WORKSPACE
                bat 'dir'
            }
        }
        
        stage('Tests') {
            parallel {
        stage('Unit') {
            steps {
                bat '''
                  set  PYTHONPATH=%WORKSPACE%
                  pytest --junitxml=result-unit.xml test/unit
                  '''
            }
        }
        stage('Rest') {
            steps {
                catchError(stageResult: 'UNSTABLE',  buildResult : 'FAILURE') {
                    bat '''
                     set FLASK_APP=app/api.py
                     start flask run
                     set PYTHONPATH=%WORKSPACE%
                     pytest --junitxml=result-rest.xml test/rest
                  '''
                }  
            }
  
         }  
            }

        }
        stage('Result') {
            steps {
               junit 'result*.xml'
               echo ' Test completed'
            }
        }

    }
}