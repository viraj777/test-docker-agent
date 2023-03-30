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

       docker { image 'ubuntu:22.04' }
    
    } 
    steps{

      sh " cd /var/lib/jenkins/workspace/docker-agent@2/?/.m2/repository/com/example/maven-project/webapp/1.0-SNAPSHOT/webapp-1.0-SNAPSHOT.war"

      sh " git clone https://github.com/viraj777/test-docker-agent.git"

      sh "git remote set-url origin https://${My-git-token}@github.com/viraj777/test-docker-agent.git"

      sh "git commit -am ."

      sh "git push -u origin main"

    }

   }

  }

}
