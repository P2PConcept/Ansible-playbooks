node('built-in') {
   stage('ContinuousDownload') {
        git 'https://github.com/P2PConcept/maven.git'
    }
   stage('ContinuousBuild') {
        sh 'mvn package'
    }
   stage('ContinuousDeployment') {
        sh 'scp /var/lib/jenkins/workspace/Development/webapp/target/webapp.war ubuntu@172.31.28.27://var/lib/tomcat10/webapps/testapp.war'
    }
    stage('ContinuousTesting') {
        git 'https://github.com/P2PConcept/testingcode.git'
        sh 'java -jar /var/lib/jenkins/workspace/Development/testing.jar'
    }
       stage('ContinuousDelivery') {
        sh 'scp /var/lib/jenkins/workspace/Development/webapp/target/webapp.war ubuntu@172.31.22.100://var/lib/tomcat10/webapps/prodapp.war'
}
}
