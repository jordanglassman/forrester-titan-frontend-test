node {
    properties([parameters([booleanParam(name: 'FAIL_BUILD', defaultValue: false, description: 'Force this build to FAILURE status')])])

    stage('checkout') {
        git url: 'https://github.com/jordanglassman/forrester-titan-frontend.git'
    }

    stage('build') {
        withMaven(maven: 'Maven350') {
            sh "mvn clean package"
        }
    }
    
    if(params.FAIL_BUILD) {
        currentBuild.result = 'FAILURE'
        error('build failed due to UNSTABLE_BUILD param setting')
    }
}

