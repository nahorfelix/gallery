pipeline {
    agent any

    tools {
        nodejs "node"
    }

    environment {
        EMAIL_RECIPIENT = 'felix.mwendwa3@student.moringaschool.com'
        RENDER_DEPLOY_HOOK = 'https://api.render.com/deploy/srv-cu0n0li3esus73bb87eg?key=UPNqA6LpeCI'
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

        stage("Deploy to Render") {
            steps {
                echo 'Deploying application to Render...'
                sh "curl -X POST ${RENDER_DEPLOY_HOOK}"
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!!'
            sh './performCleanUp.sh'
        }
        failure {
            mail to: "${EMAIL_RECIPIENT}",
                 subject: 'Pipeline Failure Notification',
                 body: 'The pipeline failed at some stage. Please check Jenkins logs for details.'
        }
        always {
            echo 'Pipeline execution complete!!'
        }
        aborted {
            echo 'Pipeline execution aborted!!'
        }
    }
}
