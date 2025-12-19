pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'step 1'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'step 2'
        sh 'mvn test'
      }
    }

    stage('package') {
      steps {
        echo 'step 3'
        sh '''GIT_SHORT_COMMIT=$(echo $GIT_COMMIT | cut -c 1-7)

mvn versions::set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions::commit'''
        sh 'mvn package -DskipTests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'maven 3.9.6'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}