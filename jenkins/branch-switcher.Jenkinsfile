@NonCPS
boolean isDevelop() {
    return env.BRANCH_NAME == 'develop'
}

@NonCPS
boolean isMain() {
  return env.BRANCH_NAME == 'main'
}

@NonCPS
boolean isPR() {
  return env.CHANGE_TARGET ? true : false
}



node {
  if (isDevelop()) {
    pipeline = readTrusted('jenkins/develop.Jenkinsfile')
  } else if (isMain()) {
    pipeline = readTrusted('jenkins/main.Jenkinsfile')
  } else if (isPR()){
    pipeline = readTrusted('jenkins/pr.Jenkinsfile')
  } else {
    pipeline = readTrusted('jenkins/feature.Jenkinsfile')
  }
}

evaluate(pipeline)
