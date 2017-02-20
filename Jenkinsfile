node {

    stage('Github Checkout') {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '921fd840-1d71-4b06-bf5e-1c6f3141f669', url: 'git@github.com:justinsr20/tdd_django.git']]])
    }

    stage('Build Container Image') {
        sh 'docker build -t jenkins/django_app:v${BUILD_NUMBER} -t jenkins/django_app:latest .'
    }

    stage('Run Unit Tests') {
        sh 'docker run jenkins/django_app /usr/src/app/run_tests.sh'
    }

    stage('Run App') {
            sh 'docker-compose up -d'
    }

}