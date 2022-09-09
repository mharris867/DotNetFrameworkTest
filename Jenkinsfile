pipeline {
    agent {label 'windows'}
    options {
    // ansiColor('xterm')
    timestamps()
  }
    stages {
        stage('Build') {            
            steps {
                powershell '''
                    Write-Host "Compiling package for:  msbuild.exe /p:Configuration=Release $ENV:VS_SOLUTION"
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
