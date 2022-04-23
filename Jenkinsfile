#!groovy

pipeline {
    agent any

    options {
        ansiColor('xterm')
    }

    environment {
        dagger = tool name: 'dagger', type: 'com.cloudbees.jenkins.plugins.customtools.CustomTool' 
    }

    stages {

        stage('checkout source') {
            steps {
                git(branch: 'main', url: 'https://github.com/FooBarQuaxx/dagger-hello-world.git')
            }
        }

        stage('test') {
            steps {
                sh "${env.dagger} version"
                sh "${env.dagger} do hello --log-format plain"
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
