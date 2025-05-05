pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
        git branch: 'master', url: 'https://github.com/Deepak93kumar/maven-project.git'
      }
    }

    stage('package job') //valiadte compile and then package
    {
      steps {
          withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn package'
          }
        }
    }
  }
}