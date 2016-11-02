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
            sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
        } else {
            bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
        }
    }
    stage('Results') {
        //   junit '**/target/surefire-reports/TEST-*.xml'
        archive 'target/*.jar'
        pwd()
//        sh '''echo "test"
//            echo $(PWD)'''
        sh "echo testingPipeline"

    }

    stage('Nexus Deployment') {
        sh 'echo Test'
    }
}