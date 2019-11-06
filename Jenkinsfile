pipeline {
    agent { docker { image 'python:3.7.2' } }
    stages {
        stage('build') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('test') {
            steps {
                sh 'python test.py'
            }
            post {
                always {
                    junit 'test-reports/*.xml'
                }
            }    
        }

        stage('deploy') { 
            steps {
                echo '... Deploying 1'
                sh 'pyinstaller --onefile app.py' 
                echo '... ... Deploying 2'
                sh 'python --version'
                sh 'pwd'
                echo '... ... ... Deploying 3'
            }
            post {
                success {
                    echo '... Post processing 1'
                    // archiveArtifacts 'dist/add2vals' 
                    sh 'whoami'
                    sh 'pwd'
                    sh 'ls dist/'
                    echo '... Post processing 2'
                }
            }            
        }
    }
}