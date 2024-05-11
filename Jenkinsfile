pipeline {
  environment {
    registry = "akenkour/20-jenkinspushregistry"
    registryCredential = 'docker-creds'
    dockerImage = '20-jenkinspushregistry'
  }
  
  agent any
  
  stages {
    
    stage('Cloning Git') {
      steps {
        git 'https://github.com/rakenkou-github/20-jenkinspushregistry.git'
      }
    }
    
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }

/*     
    
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
    */
  }
}
