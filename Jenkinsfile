pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Zalupa'
        sh 'ls'
        sh '''



sh run_build_script.sh'''
      }
    }

    stage('Linux') {
      steps {
        echo 'Run Linux Script'
        sh 'sh run_linux_tests.sh'
      }
    }

    stage('Deploy Staging') {
      steps {
        echo 'Deploy to staging environment'
      }
    }

    stage('Deploy production') {
      steps {
        echo 'Deploy to Prod'
      }
    }

  }
  post {
    always {
      archiveArtifacts(artifacts: 'target/demoapp.jar', fingerprint: true)
    }

    failure {
      mail(to: 'ci-team@example.com', subject: "Failed Pipeline ${currentBuild.fullDisplayName}", body: " For details about the failure, see ${env.BUILD_URL}")
    }

  }
}