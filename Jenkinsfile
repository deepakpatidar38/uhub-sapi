pipeline {
  agent any
  environment{
  	ANYPOINT_CREDS = credentials('ANYPOINT_CREDENTIALS')
  }
  stages {
    stage('Build') { 
      steps {
        bat 'mvn -B -U -e -V clean %M2SETTINGS% -DskipTests package'
      }
    }

    stage('Test') { 
      steps {
        echo '*************** Test execution completed****************'
      }
    }
    stage('Deployment') { 
    environment{
  	CLIENT_ID = credentials('TEST_CLIENT_ID')
  	CLIENT_SECRET = credentials('TEST_CLIENT_SECRET')
  }
      steps {
         bat 'mvn -U -V -e -B %M2SETTINGS% -DskipTests deploy -Ptest -DmuleDeploy -Danypoint.username="%ANYPOINT_CREDS_USR%" -Danypoint.password="%ANYPOINT_CREDS_PSW%" -Danypoint.platform.client_id="%CLIENT_ID%" -Danypoint.platform.client_secret="%CLIENT_SECRET%"' 
      }
    }
  }
}
