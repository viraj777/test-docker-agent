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
  }

}
