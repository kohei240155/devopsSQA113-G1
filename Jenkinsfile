pipeline {
    agent any

    environment {
        FIREBASE_DEPLOY_TOKEN = credentials('firebase-token')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Installing Firebase Tools...'
                sh 'npm install -g firebase-tools || true'
                sh 'firebase --version'
            }
        }

        stage('Testing') {
            steps {
                echo 'Deploying to Testing environment...'
                sh 'firebase deploy --project finalexam-testing-c27df --token "$FIREBASE_DEPLOY_TOKEN" --only hosting'
            }
        }

        stage('Staging') {
            steps {
                echo 'Deploying to Staging environment...'
                sh 'firebase deploy --project finalexam-staging-d45a7 --token "$FIREBASE_DEPLOY_TOKEN" --only hosting'
            }
        }

        stage('Production') {
            steps {
                echo 'Deploying to Production environment...'
                sh 'firebase deploy --project finalexam-production-aa40f --token "$FIREBASE_DEPLOY_TOKEN" --only hosting'
            }
        }
    }
}