// pipeline {
//     agent any

//     stages {
//         stage('Checkout') {
//             steps {
//                 checkout scm
//             }
//         }

//         stage('Check Environment') {
//             steps {
//                 sh 'echo "===== WORKSPACE ====="'
//                 sh 'pwd'
//                 sh 'echo "===== FILES ====="'
//                 sh 'ls -la'
//                 sh 'echo "===== PYTHON ====="'
//                 sh 'which python3 || true'
//                 sh 'python3 --version'
//                 sh 'echo "===== VENV MODULE ====="'
//                 sh 'python3 -m venv --help >/dev/null'
//             }
//         }
//         stage('Create Virtual Environment') {
//             steps {
//                 sh 'python3 -m venv .venv'
//                 sh '.venv/bin/python --version'
//                 sh '.venv/bin/pip --version'
//             }
//         }
//         stage('Install Dependencies') {
//             steps {
//                 sh '.venv/bin/python3 -m pip install --upgrade pip'
//                 sh '.venv/bin/python3 -m pip install -r requirements.txt'
//                 sh '.venv/bin/python3 -m pip list'
//             }
//         }

//         stage('Run Tests') {
//             steps {
//                 sh 'mkdir -p reports'
//                 sh '.venv/bin/python3 -m pytest tests --junitxml=reports/junit.xml --html=reports/report.html --self-contained-html'
//                 sh 'ls -la reports'
//             }
//         }
//     }

//     post {
//         always {
//             archiveArtifacts artifacts: 'reports/**', allowEmptyArchive: true
//             junit testResults: 'reports/junit.xml', allowEmptyResults: true

//             publishHTML(target: [
//                 allowMissing: true,
//                 alwaysLinkToLastBuild: true,
//                 keepAll: true,
//                 reportDir: 'reports',
//                 reportFiles: 'report.html',
//                 reportName: 'Pytest HTML Report'
//             ])
//         }
//     }
// }

pipeline {
    agent any
    
    stages {
        stage("A") {
            steps {
                sh "pwd"
            }
        }
        stage("B") {
            steps {
                sh "python3 --version"
            }
        }
    }
}