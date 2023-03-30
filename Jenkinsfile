pipeline{
  agent any

  stages{
    stage('build'){
    agent{
      
      docker { image 'maven:latest' }

    }
    steps{
    
      git branch: 'main', url: 'https://github.com/viraj777/test-docker-agent.git'

      sh "mvn clean install"

    }
   }
  }

}
