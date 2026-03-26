pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check Environment') {
            steps {
                sh 'echo "===== WORKSPACE ====="'
                sh 'pwd'
                sh 'echo "===== FILES ====="'
                sh 'ls -la'
                sh 'echo "===== PYTHON ====="'
                sh 'which python3 || true'
                sh 'python3 --version'
                sh 'echo "===== PIP ====="'
                sh 'python3 -m pip --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m pip install --upgrade pip'
                sh 'python3 -m pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mkdir -p reports'
                sh 'python3 -m pytest tests --junitxml=reports/junit.xml'
                sh 'ls -la reports'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'reports/**/*', allowEmptyArchive: true
            junit testResults: 'reports/junit.xml', allowEmptyResults: true
        }
    }
}