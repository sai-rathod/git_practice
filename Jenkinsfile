@Library("shared") _
pipeline{
    agent any
    stages{
        stage("fetch"){
            steps{
                script{
                    clone("https://github.com/sai-rathod/git_practice.git","main")
                    echo "code clonned successfully"
                }
            }
        }
        stage("build"){
            steps{
                script{
                    push("react-app","latest")
                    echo "image building completed"
                }
            }
        }
        stage("deploy"){
            steps{
                withCredentials([usernamePassword(credentialsId:'dockerCred',
                usernameVariable:'dockerUser',passwordVariable:'dockerPass')]){
                    sh '''
                    docker run -d -p 3000:3000 $dockerUser/react-app:latest
                    echo "app successfully deployed"
                    '''
                }
            }
        }
    }
}
