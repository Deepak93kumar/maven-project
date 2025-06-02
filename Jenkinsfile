pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
        git branch: 'master', url: 'https://github.com/Deepak93kumar/maven-project.git'
      }
    }

    stage('compile the job') //validate then compile
    {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn compile'
        }
      }
    }
    stage('build the code') {
      steps {
        withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn clean  package'
        }
      }
    }
    stage('create docker image') {
      steps {
        sh 'docker build -t deepak354/deepak:latest .'
      }
    }
    stage('push docker image to dockerhub') {
      steps {
        
        ithDockerRegistry(credentialsId: 'DockerHubCredentials', url: 'https://index.docker.io/v1/') {
            
                sh 'docker push deepak354/deepak:latest'
        }
      }
    }
  }
}

