pipeline{
   agent any 
   
    tools{
        maven 'Maven2'
        jdk 'JDK7'
    }
  
  stages {
      stage("Maven Build"){
          steps{
              sh 'mvn -B -DskipTests clean package'
          }
      }
      
     stage("Build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('sonar-test') {
                sh 'java -version'
                sh 'mvn clean package sonar:sonar'
              }
            }
          }
     /*stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    
     stage('Deploy to artifactory'){
        steps{
        rtUpload(
         serverId : 'ARTIFACTORY_SERVER',
         spec :'''{
           "files" :[
           {
           "pattern":"target/*.jar",
           "target":"art-doc-devo-loc"
           }
           ]
         }''',
         
      )
      }
     }*/
  } 
    
  }

           
