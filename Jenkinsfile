/**
* Android Jenkinsfile
*/
def isValidPlatform = {name ->
  ['android', 'ios'].contains(name)
}

def platformName = params?.FH_PLATFORM_NAME?.trim()

stage('Check Node') {
  if (!isValidPlatform(platformName)) {
    error("invalid platform ${platformName}")
	}
}

node(platformName) {
    stage 'Checkout'
    checkout scm

    stage 'Prepare'
    writeFile file: 'app/src/main/assets/fhconfig.properties', text: params.FH_CONFIG_CONTENT

    stage 'Done'
    sh 'cat app/src/main/assets/fhconfig.properties'
}
