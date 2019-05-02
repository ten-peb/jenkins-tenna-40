node("master"){
  def String repo = 'git@github.com:ten-peb/jenkins-tenna-40-web.git'
  def String cloneto = 'work' 
  stage("clone myself"){
    sh('rm -rf work')  // clean up before cloning
    doGitClone(repo,cloneto)
  }
  stage("gather artifacts"){
    dir(cloneto){
      sh('cp -rp /data/staging/ui ui/') // clone frontend artifacts
      sh('cp -rp /data/staging/backend backend/') // clone backend artifacts
    }
  }
  stage("spinup containers"){
      sh('docker-compose up -d --build')
  }
  stage("notify qa"){
  }
}