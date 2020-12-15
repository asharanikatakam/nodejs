pipeline {
  agent {
    docker {
      image 'node:4-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('build') {
      parallel {
        stage('build') {
          steps {
            sh 'npm install'
          }
        }

        stage('test') {
          steps {
            sh '''npm install
npm test'''
          }
        }

        stage('package') {
          steps {
            sh '''npm run package
archiveArtifacts \'*/distribution/.zip\''''
          }
        }

      }
    }

  }
}