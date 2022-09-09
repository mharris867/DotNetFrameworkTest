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
                    Invoke-Expression "msbuild.exe /p:Configuration=Release ./testlibrary/testlibrary.csproj"
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
