pipeline {
    agent any

    tools {
        // specify required tools based on jenkins global tool configruation names
        jdk 'JDK'
        maven 'MAV'
    }

    stages {
        stage('Initialize') {
            steps {
                script {
                    // list of repo-branch pairs to build
                    def buildConfigurations = [
                        [repo: 'https://github.com/nabilelbajdi/hello-world.git', branch: '1'],
                        [repo: 'https://github.com/nabilelbajdi/hello-world.git', branch: '2'],
                        [repo: 'https://github.com/nabilelbajdi/hello-world2.git', branch: 'a'],
                        [repo: 'https://github.com/nabilelbajdi/hello-world2.git', branch: 'b']
                    ]

                    // iterate over each repo-branch pair and build them in sequence
                    for (config in buildConfigurations) {
                        // print current repository and branch being built to jenkins console
                        echo "Building ${config.repo} on branch ${config.branch}"
                        
                        // checkout the repo and branch
                        git branch: config.branch, url: config.repo
                        
                        // run maven build command
                        sh 'mvn clean install'
                        
                    }
                }
            }
        }
    }
}
