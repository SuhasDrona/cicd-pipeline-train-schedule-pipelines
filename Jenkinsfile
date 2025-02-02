pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
    }
}

// pipeline {

//     agent {
//         label 'agentId' //The id of the slave/agent where the build should be executed, if it doesn't matter use "agent any" instead.
//     }

//     triggers {
//         cron('H */8 * * *') //regular builds
//         pollSCM('* * * * *') //polling for changes, here once a minute
//     }

//     stages {
//         stage('Checkout') {
//             steps { //Checking out the repo
//                 checkout changelog: true, poll: true, scm: [$class: 'GitSCM', branches: [[name: '*/master']], browser: [$class: 'BitbucketWeb', repoUrl: 'https://web.com/blah'], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'git', url: 'ssh://git@git.giturl.com/test/test.git']]]
//             }
//         }
//         stage('Build') {
//             steps {
//                 script {
//                    sh './gradlew clean test --no-daemon' //run a gradle task
//                 }
//             }
//         }
//         stage('Frontend Unit Tests') {
//             steps {
//                 sshagent(['git']) {
//                     script {
//                         try {
//                             sh './gradlew cleanFrontendTest --no-daemon'
//                             sh './gradlew frontendUnitTest --no-daemon'
//                         } finally {
//                             junit 'publicapi/frontend/test/karma-result.xml'
//                         }
//                     }
//                 }
//             }
//         }
//         stage('Frontend Static Code Analysis') {
//             steps {
//                 script {
//                     try {
//                         sh './gradlew tslint --no-daemon'
//                     } finally { //Make checkstyle results available
//                         checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: 'publicapi/frontend/tslint-result.xml', unHealthy: ''
//                     }
//                 }
//             }
//         }
//         stage('End 2 End Tests') {
//             steps {
//                 script {
//                     try {
//                         sh './gradlew e2e --no-daemon'
//                     } finally { //Make selenium/protractor results available and publish the html (containing screenshots)
//                         junit '**/e2e-results/junit-formatted/*.xml'
//                         publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'publicapi/frontend/test/e2e-results/html-formatted/', reportFiles: 'htmlReport.html', reportName: 'End 2 End Test Report', reportTitles: ''])
//                     }
//                 }
//             }
//         }
//         stage('Publish Artifact to Nexus') {
//             steps {
//                 sh './gradlew publish --no-daemon'
//             }
//         }
//     }
// }
