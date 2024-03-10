pipeline {
    agent any
    parameters {
        string(name: 'REPO_URL', defaultValue: 'https://github.com/nabilelbajdi/hello-world', description: 'Repository URL to build.')
        string(name: 'BRANCH_NAMES', defaultValue: 'main', description: 'Comma-separated list of branches to build.')
    }
    tools {
        jdk 'JDK'
        maven 'MAV'
    }
    stages {
        stage('Initialize and Build') {
            steps {
                script {
                    def branches = params.BRANCH_NAMES.tokenize(',').collect { it.trim() }
                    branches.each { branch ->
                        echo "Checking out and building branch: ${branch}"
                        checkout([$class: 'GitSCM', branches: [[name: branch]], userRemoteConfigs: [[url: params.REPO_URL]]])
                        sh 'mvn clean install'
                    }
                }
            }
        }
    }
}
