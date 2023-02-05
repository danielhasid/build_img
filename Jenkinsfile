pipeline {
    agent any
    environment {
    registry = "dhasid1/daniel_repository"  // he name of your user and repository (which can be created manually)
    registryCredential ='Docker1' // The credentials used to your repo
    dockerImage = "img1" // will be overridden later
  }
    stages{
        stage('build and push image') {
            steps {
               script {
                   echo "$BUILD_NUMBER"
                    dockerImage = docker.build registry + ":$BUILD_NUMBER" // give a name and version to image
                   docker.withRegistry('', registryCredential) 
                    dockerImage.push() // push image to hub
                }
            }
        }
    }

}
