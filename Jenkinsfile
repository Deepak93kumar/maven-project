pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
        git branch: 'master', url: 'https://github.com/kumargaurav039/maven-project.git'
      }
    }

    stage('package the job') //valiadte then compile
    {
      steps {
          withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn compile'
          }
        }
      }
    }
}