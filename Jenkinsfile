pipeline {
    agent none

    environment {
        DOTNET_CLI_HOME = "/tmp/dotnet_cli_home"
    }

    stages {
        stage('Build & test .net ') {
            agent {
               docker { image 'mcr.microsoft.com/dotnet/sdk:5.0' }
            }
            steps {
                sh "dotnet build"
                sh "dotnet test"
            }
        }
        stage('Build and test node') {
            agent {
               docker { image 'node:14' }
            }
            steps {
                dir('DotnetTemplate.Web') {
                    sh "npm i"
                    sh "npm run build"
                    sh "npm run lint"
                    sh "npm test"
                }
            }
        }
    }
}