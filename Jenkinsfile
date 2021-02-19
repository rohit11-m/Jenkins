@Library('piper-lib-os') _

abapEnvironmentPipeline script: this

pipeline {
  agent any

  stage('prepare') {
    checkout scm
    setupCommonPipelineEnvironment script:this
    checkChangeInDevelopment script: this
  }

  stage('buildMta') {
    mtaBuild script: this
  }

  stage('uploadToTransportRequest') {
    transportRequestCreate script: this
    transportRequestUploadFile script:this
    transportRequestRelease script: this
  }

}
