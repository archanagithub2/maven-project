git credentialsId: '8628a8b0-b062-4631-882f-ff8c5f022610', url: 'https://github.com/jleetutorial/maven-project.git'

pipeline{
    agent any
  tools{
      maven 'mvn 3.6.3'
      jdk 'jdk 11.0.5'
  }
    
    stages{
        stage('cloning')
        {
            steps{
          git credentialsId: '8628a8b0-b062-4631-882f-ff8c5f022610', url: 'https://github.com/jleetutorial/maven-project.git/'
            }
        }
        
        stage('compile')
        {
            steps{
                sh 'mvn clean compile'
            }
        }
        stage('test')
        {
            steps{
                sh 'mvn test'
            }
        }
        stage('build')
        {
            steps{
              sh 'mvn -Dmaven.test.failure.ignore=true clean package'
            }
            post{
                success{
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
        
    }
    
}
