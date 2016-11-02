#!groovy
node {
    def mvnHome
    stage('Preparation') { // for display purposes
        // Get some code from a GitHub repository
        git url: 'https://github.com/lecourtoisn/jenkinsTests.git'

        // Get the Maven tool.
        // ** NOTE: This 'M3' Maven tool must be configured
        // **       in the global configuration.
        mvnHome = tool 'M3'
    }
    stage('Build') {
        // Run the maven build
        if (isUnix()) {
            sh "'${mvnHome}/bin/mvn' clean package"
        } else {
            bat(/"${mvnHome}\bin\mvn" clean package/)
        }
    }

    stage('Nexus Deployment') {

        if (isUnix()) {
            sh "'${mvnHome}/bin/mvn' -X deploy"
        } else {
            bat(/"${mvnHome}\bin\mvn" -X deploy/)
        }
    }
}