pipeline {
  agent any
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
      steps {
         bat 'mvn -U -V -e -B %M2SETTINGS% -DskipTests deploy -Ptest -DmuleDeploy' 
      }
    }
  }
}
