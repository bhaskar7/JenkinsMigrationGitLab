pipeline {
	agent any
  
environment {

  LT_USERNAME = "techwithmoss"
  MAVEN_CLI_OPTS = " --batch-mode -DsuiteXmlFile=testng.xml"
}
stages {
  stage('test') {
    steps {
    withMaven(maven:'Maven3', options: [junitPublisher(healthScaleFactor: 1.0)]) {
      withCredentials([string(credentialsId: 'LT_ACCESS_TOKEN', variable: 'LT_ACCESS_TOKEN')]) {
      sh '''
        mvn $MAVEN_CLI_OPTS test
    '''

    }
    }
    }
  }

}
}
