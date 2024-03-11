pipeline {
    agent any

    parameters {
        string(name: 'REPO', defaultValue: 'https://github.com/nabilelbajdi/hello-world.git', description: 'Repository to build')
        string(name: 'BRANCH', defaultValue: 'main', description: 'The name of the branch to build')
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the specified repo and branch
                git branch: "${params.branchName}", url: "${params.repoUrl}"
            }
        }
        
        stage('Build') {
            steps {
                // Run the Maven build
                sh 'mvn clean install'
            }
        }
    }
}
