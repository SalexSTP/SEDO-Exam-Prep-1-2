pipeline{
    agent any
    stages{
        stage("Restore dependencies"){
            when {
                anyOf {
                    branch "main"
                    branch "feature"
                }
            }
            steps{
                bat "dotnet restore"
            }
        }
        stage("Build project"){
            when {
                anyOf {
                    branch "feature"
                    branch "develop"
                }
            }
            steps{
                bat "dotnet build --no-restore"
            }
        }
        stage("Run tests"){
            when {
                anyOf {
                    branch "feature"
                    branch "develop"
                }
            }
            steps{
                bat "dotnet test --no-build --verbosity normal"
            }
        }
    }
}
