pipeline{
  agent any

  stages{
    stage('build'){
    environment{
         
       My-git-token = credentials('Github-access')

    }
    agent{
      
      docker { image 'maven:3.8.7-eclipse-temurin-11' }

    }
    steps{
    
      git branch: 'main', url: 'https://github.com/viraj777/test-docker-agent.git'

      sh "mvn clean install"

      sh "git remote set-url origin https://${My-git-token}@github.com/viraj777/test-docker-agent.git"

      sh "git commit -am ."

      sh "git push -u origin main"

    }
   }
  }

}
