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

       docker { image 'ubuntu:latest' }
    
    } 
    steps{

      sh " cp -r /var/lib/jenkins/workspace/docker-agent@2/?/.m2/repository/com/example/maven-project/webapp/1.0-SNAPSHOT/  ./app"

      sh " cd ./app"

      sh " echo '${My_git_token}'"


    }

   }

  }

}
