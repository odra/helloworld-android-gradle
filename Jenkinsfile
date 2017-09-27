/**
* Android Jenkinsfile
*/
node("android") {
  stage("Checkout"){
    checkout scm
  }

  stage ("Prepare") {
    writeFile file: 'app/src/main/assets/fhconfig.properties', text: params.FH_CONFIG_CONTENT
    sh 'gem install fastlane'
  }

  stage("Build") {
    sh 'chmod +x ./gradlew'
    sh "fastlane build clean:true config:${params.BUILD_CONFIG}"
  }

  stage("Sign") {
    if (params.BUILD_CONFIG == 'release') {
        println('Not supported yet!')
    } else {
      println('Debug Build - Using default developer signing key')
    }
  }

 stage("Archive") {
    if (params.BUILD_CONFIG == 'release') {
        archiveArtifacts artifacts: 'app/build/outputs/apk/app-release.apk', excludes: 'app/build/outputs/apk/*-unaligned.apk'
    } else {
        archiveArtifacts artifacts: 'app/build/outputs/apk/app-debug.apk', excludes: 'app/build/outputs/apk/*-unaligned.apk'
    }
  }
}
