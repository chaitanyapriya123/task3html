def imagename = "chaitanyapriya/htmlimage"
def dockerImage = ''
 node {
     stage('Cloning Git') {
         git(url: 'https://github.com/chaitanyapriya123/task3html.git', branch: 'main')
       }
      stage('Building image') {
         script {
         dockerImage = docker.build imagename
      }
    }
      stage('Deploy Image') {
          withCredentials([usernamePassword(credentialsId: 'Docker', passwordVariable: 'DockerPassword', usernameVariable: 'DockerUser')]) {
            sh "docker login -u ${env.DockerUser} -p ${env.DockerPassword}"
            sh 'docker push chaitanyapriya/htmlimage:latest'
            sh "docker pull chaitanyapriya/htmlimage:latest"
            sh "docker run -d -t -p 3000:3000 --name mycontainer${BUILD_NUMBER}. chaitanyapriya/htmlimage:latest "
      }
    }  
 } 
