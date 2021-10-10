// @Library('piper-lib') _

// piperPipeline script: this


@Library('piper-lib-os') _


pipeline {

    agent any

    stages {
        stage("prepare") {
            steps {
                deleteDir()
                checkout scm
                setupCommonPipelineEnvironment script: this
            }
        }

        stage('build') {
            steps {
                // It depends on your project, what needs to be done here. Maybe it's sufficient to zip the sources
//                 mtaBuild script: this
                buildExecute script:this, buildTool: 'npm'
            }
        }

//         stage('publish') {
//             steps {
//                 // This uploads the binary into a blob store so that it can be attached to a transport request later
//                 sh "curl --upload-file <deployable> <BLOB_STORE/path/to/application>"

//                 // OR (in case there is no BLOB_STORE available)

//                 // This makes the artifact available on Nexus. The URL is the following:
//                 // <JENKINS_URL>/job/<JOB_NAME>/<BUILD_NUMBER>/artifact/<DEPLOYABLE>. Nota bene: this format is not an Jenkins API.
//                 // The build number can be retrieved during the build through ${currentBuild.number}
//                 archiveArtifacts artifacts: <deployable>
//             }
//         }

//         // This attaches the deployable to a transport request
//         stage('attach') {
//             steps {
//                 transportRequestUploadRFC script: this,
//                                            transportRequestId: '<TRANSPORT_REQUEST_ID>', // This can be omitted if present inside a Git commit message
//                                            applicationUrl: '<THE_URL_TO_THE_DEPLOYABLE_ACCORDING_TO_PUBLISH_STAGE>'
//             }
//         }
    }
}
