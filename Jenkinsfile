pipeline {
  agent any
  environment{
  	ANYPOINT_CREDS = credentials('ANYPOINT_CREDENTIALS')
  }
  stages {
    stage('Build') { 
      steps {
        bat 'mvn -B -U -e -V clean -gs %M2SETTINGS% -DskipTests package'
      }
    }
<<<<<<< HEAD
    stage('Test') { 
=======
    stage('Test') { 
>>>>>>> 03341c3c41ca6df871f691f3e83a8bd43f359105
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
         bat 'mvn -U -V -e -B -gs %M2SETTINGS% -DskipTests deploy -DmuleDeploy -Danypoint.username="%ANYPOINT_CREDS_USR%" -Danypoint.password="%ANYPOINT_CREDS_PSW%" -Danypoint.platform.client_id="%CLIENT_ID%" -Danypoint.platform.client_secret="%CLIENT_SECRET%"' 
      }
    }
  }
}
