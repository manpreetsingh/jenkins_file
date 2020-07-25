pipeline {
   agent any

   tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "maven3"
   }

   stages {
      stage('Git Checkout') {
         steps{
            // Get some code from a GitHub repository
            git 'https://github.com/manpreetsingh/anothermaven.git'
         }
      }
      stage('Maven Build') {
         steps {

            // Run Maven on a Unix agent.
            sh "mvn clean package"
         }

         post {
            // If Maven was able to run the tests, even if some of the test
            // failed, record the test results and archive the jar file.
            success {
               archiveArtifacts 'target/*.war'
            }
         }
      }
   }
}

