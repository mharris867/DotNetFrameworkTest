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
                    Write-Host "Compiling package for:  msbuild.exe /p:Configuration=Release ./testlibrary/testlibrary.csproj"
                    Invoke-Expression "msbuild.exe /p:Configuration=Release ./testlibrary/testlibrary.csproj"
                '''
            }
        }
        stage('Test') {
            steps {
                powershell '''
                    Write-Host "Restoring: msbuild.exe -t:restore ./UnitTestProject1/UnitTestProject1.sln"
                    Invoke-Expression "msbuild.exe -t:restore ./UnitTestProject1/UnitTestProject1.sln"
                    Write-Host "Compiling: msbuild.exe /p:Configuration=Release ./UnitTestProject1/UnitTestProject1.sln"
                    Invoke-Expression "msbuild.exe /p:Configuration=Release ./UnitTestProject1/UnitTestProject1.sln /consoleloggerparameters:ForceConsoleColor"
                    Write-Host "Running:  vstest.console.exe """"$ENV:GRUNT_TESTS"""" /Enablecodecoverage /InIsolation /Logger:trx"
                    & vstest.console.exe """"$ENV:GRUNT_TESTS"""" /Enablecodecoverage /InIsolation /Logger:trx
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
