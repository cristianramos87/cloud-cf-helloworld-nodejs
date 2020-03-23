@Library('piper-lib-os') _
node() {
  stage('prepare') {
//   sh '/var/jenkins_home/repositories/mycommit.sh'
    checkout scm
    setupCommonPipelineEnvironment script:this
    checkChangeInDevelopment script: this    
  }
  stage('buildMta') {
    mtaBuild script: this
  }  
  stage('create_TR') {
    def transportRequestId = transportRequestCreate script: this
  }
  stage('upload_MTA') {
    transportRequestUploadFile script: this
  }   
}
