node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
    git credentialsId: '18b8a613-ed3d-40a7-8656-4485399720ec', url: 'git@github.com:shivangi-jaiswal/jenkins_test.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'maven3'
      env.JAVA_HOME ="${tool 'jdk2'}"
      env.PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
   }
   
   stage('Build') {
      // Run the maven build
     
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -f api-gateway/pom.xml -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      archiveArtifacts 'api-gateway/target/*.jar'
   }
}
