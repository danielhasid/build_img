pipeline {
    environment {
    registry = "danielhasid/build_img"  // he name of your user and repository (which can be created manually)
    registryCredential = 'ckfa' // The credentials used to your repo
    dockerImage = "python_img" // will be overridden later
  }
        stage('build and push image') {
            steps {
               script {
                    dockerImage = docker.build registry + :1 // give a name and version to image
                   docker.withRegistry(", registryCredential) {
                    dockerImage.push() // push image to hub
                }
            }
        }
        
         post {
         always {
             bat "docker rmi $registry 1" // delete the local image at the end
         }}}
