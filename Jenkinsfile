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
        stage('Checkout and Build') {
            steps {
                script {
                    def branches = params.BRANCH_NAMES.tokenize(',')
                    branches.each { branch ->
                        echo "Checking out branch: ${branch} from ${params.REPO_URL}"
                        // clean the workspace before checking out a new repo/branch to avoid conflicts.
                        deleteDir() 
                        git branch: branch, url: params.REPO_URL
                        // run the build command inside the loop to ensures that it's executed in the context of each checked-out branch.
                        sh 'mvn clean install'
                    }
                }
            }
        }
    }
}
