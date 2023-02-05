pipeline {
    environment {
    registry = "dhasid1/daniel_repository"  // he name of your user and repository (which can be created manually)
    registryCredential ='ckfa1' // The credentials used to your repo
    dockerImage = "" // will be overridden later
  }
        stage('build and push image') {
            steps {
               script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER" // give a name and version to image
                   docker.withRegistry(", registryCredential) {
                    dockerImage.push() // push image to hub
                }
            }
        }
        
         post {
         always {
             bat "docker rmi $registry:$BUILD_NUMBER" // delete the local image at the end
         }}}
