@Library("sharedlibrary") _
 pipeline {
  agent {
        label 'linux'
    }
    stages {
      stage('Maven Build') {
        steps {
          sh 'mvn clean package'
      }
    }
    stage('Deploy to Tomcat') {
      steps {
        tomcatDeploy('10.20.0.152','app','tomcat')
      }
    }
  }
  post {
    success {
      archiveArtifacts artifacts: 'target/*.war'
      cleanWs()
    }
  }
}
