/**
* Android Jenkinsfile
*/
node('android') {
    stage 'Checkout'
    checkout scm

    stage 'Build'
		sh 'env | grep FH_' 
    sh "./gradlew clean assembleDebug"

    stage 'Archive'
    archive 'app/build/outputs/apk/*.apk'
}
