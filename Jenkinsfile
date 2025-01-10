pipeline {
    agent any

    tools {
        nodejs "node"
    }



    triggers {
        githubPush()
    }

    stages {
        stage("Clone Repository") {
            steps {
                git branch: "master", url: "https://github.com/nahorfelix/gallery"
            }
        }

        stage("Install Dependencies") {
            steps {
                sh 'npm install'
            }
        }

        stage("Run Tests") {
            steps {
                sh 'npm test'
            }
        }

      }
    post {
        success {
            echo 'Pipeline completed successfully!!'
            sh './performCleanUp.sh'
        }

        always {
            echo 'Pipeline execution complete!!'
        }
        aborted {
            echo 'Pipeline execution aborted!!'
        }
    }
}
