#!/usr/bin/env groovy

pipeline {

    agent {
        docker {
            image 'node'
            args '-u root'
        }
    }

    stages {
        stage('Build') {
         steps {
            browserstack(credentialsId: '0cfd25c7-093e-4833-85fb-a6fb7f4b671f') {
               // some example test commands ...
               sh 'npm install'
               sh 'node parallel.js'
            }
             // Enable reporting in Jenkins
             browserStackReportPublisher 'automate'
         }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'npm test'
            }          
        }
    }
}
