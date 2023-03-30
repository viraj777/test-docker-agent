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

      sh " git --version"

      sh " cp -r /var/lib/jenkins/workspace/docker-agent@2/?/.m2/repository/com/example/maven-project/webapp/1.0-SNAPSHOT/  ./app"

      sh " cd ./app"

      sh " git init"

      sh " git remote add origin  https://github.com/viraj777/test-docker-agent.git"

      sh " git remote set-url origin https://${My-git-token}@github.com/viraj777/test-docker-agent.git"

      sh " git pull origin main"

      sh "git commit -am ."

      sh "git push -u origin main"

    }

   }

  }

}
