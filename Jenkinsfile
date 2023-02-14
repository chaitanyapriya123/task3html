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
          withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUser')]) {
            sh "docker login -u ${env.dockerUser} -p ${env.dockerPassword}"
            sh 'docker push chaitanyapriya/htmlimage:latest'
            sh "docker pull chaitanyapriya/htmlimage:latest"
            sh "docker run -d -t -p 3000:3000 --name mycontainer${BUILD_NUMBER}. chaitanyapriya/htmlimage:latest "
      }
    }  
 } 
