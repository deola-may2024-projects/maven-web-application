node{

echo "Job name is: ${env.JOB_NAME}"
echo "Build Number is: ${env.BUILD_NUMBER}"
echo "Jenkins Home is: ${env.JENKINS_HOME}"
echo "Build Number is: ${env.BUILD_NUMBER}"


properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome = tool name: 'maven3.9.8'

stage('CheckOutCode'){
git branch: 'development', credentialsId: '5daa7281-b290-45ed-8317-05d0c353f078', url: 'https://github.com/deola-may2024-projects/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

stage('UploadArtifactIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployAppIntoTomcat'){
sshagent(['8ff4f512-14b5-4363-9e0f-8167feb228cb']){
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@52.60.78.247:/opt/apache-tomcat-9.0.89/webapps/"
}
}
*/
}
