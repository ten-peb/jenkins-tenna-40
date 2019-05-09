node("master"){
  def String repo = 'git@github.com:ten-peb/jenkins-tenna-40-web.git'
  def String cloneto = 'work' 
  stage("clone myself"){
    sh('rm -rf work')  // clean up before cloning
    doGitClone(repo,cloneto)
  }
//  stage("gather artifacts"){
//    dir(cloneto){
//      sh('cp -rp /data/staging/ui ui/') // clone frontend artifacts
//      sh('cp -rp /data/staging/backend backend/') // clone backend artifacts
//    }
   stage("Ask Permission"){    
    def Boolean approve = false
    def String  joburl = env.BUILD_URL
    def String[] message_lines = [
    "Greetings",
    "There is a job on Jenkins requiring your approval to continue.",
    "Please follow this URL: " + joburl,
    "Go to the console output and scroll to the bottom to either",
    "give or deny approval.  This will invalidate in five days."
    ]
    def String message = message_lines.join("\n")
    sendEmail(qaTeam(),"Pending Approval (Jenkins)",message)
    timeout(time: 5,unit: 'Day') { 
      approve = getUserApproval(
      'spinup containers','about to  spin up new containers',
      'Do you approve?'
      )
    }
    if ( approve != true ) {
      continuePipeline = false
      currentBuild.result = 'FAILURE'
    }
  }
  stage("spinup containers"){
    dir(cloneto){
      sh('docker-compose up -d --build')
    }
  }
  stage("notify qa"){
    sendEmail(qaTeam(),"Build of ui/backend containers","completed successfully")
    
  }
}