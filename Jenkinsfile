#!groovy
node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      //   git 'https://github.com/lecourtoisn/jenkinsTests.git'
//      git branch: 'master', credentialsId: '0e827c54e38ca6201020ae8cca5064108e664a1e', url: 'ssh://git@github.com:lecourtoisn/jenkinsTests.git'
      git credentialsId: '2e10846d-ced1-4a15-beb5-c9716c3bea39', url: 'https://github.com/lecourtoisn/jenkinsTests.git'

      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      //   junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}