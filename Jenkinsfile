pipeline{
  agent any

  stages{
    stage('build'){
    agent{
      
      docker { image 'maven:3.8.7-eclipse-temurin-11' }

    }
    steps{
    
      git branch: 'main', url: 'https://github.com/viraj777/test-docker-agent.git'

      sh "mvn clean install"

    }
   }
    
    stage('upload artifact to github'){

    environment{

       My_git_token = credentials('Github-access')

    }
    agent{

       docker { image 'virajthorat776/ubuntu-git:latest' }
    
    } 
    steps{

      sh " git --version "

      sh " pwd "


      sh """if [ ! -d 'test-docker-agent' ]
             then
            
                git clone https://github.com/viraj777/test-docker-agent.git 
             fi"""     
             
      sh " cd test-docker-agent "



      sh " cp  /var/lib/jenkins/workspace/docker-agent@2/?/.m2/repository/com/example/maven-project/webapp/1.0-SNAPSHOT/*.war  . "


      sh """ git config  user.email 'virajthorat776@gmail.com'
             git config  user.name 'viraj777' """

      sh " git add . && git commit -m 'adding artifact to github' "

      sh " git remote set-url origin https://${My_git_token}@github.com/viraj777/test-docker-agent.git "



      sh " git push origin main "

    }

   }

  }

}
