pipeline {
  agent any
  stages {
    stage('upload') {
      steps {
        sh '''cd /home/tibco/tibco/tra/5.10/bin/
   ./AppManage -upload -ear /home/tibco/tibco/designer/5.10/ProvePoller.ear -app Prove -domain ProveJenkins -user admin -pw admin
'''
      }
    }
    stage('deploy') {
      steps {
        sh '''cd /home/tibco/tibco/tra/5.10/bin/
   ./AppManage -force -deploy -app Prove -domain ProveJenkins -user admin -pw admin -domain ProveJenkins
'''
      }
    }
    stage('start') {
      steps {
        sh '''cd /home/tibco/tibco/tra/5.10/bin/
   ./AppManage -start -app Prove -domain ProveJenkins -user admin -pw admin'''
        svn(url: 'https://app.deveo.com/catenate/projects/provesvn/repositories/subversion/svnrepo', poll: true)
      }
    }
  }
}