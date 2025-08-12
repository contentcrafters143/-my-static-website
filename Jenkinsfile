pipeline {
    agent any

    stages {
        stage('Checkout Codegit s') {
            steps {
                // This tells Jenkins to get the latest code from your GitHub repository.
                git branch: 'main', url: 'https://github.com/<your-username>/my-static-website.git'
            }
        }

        stage('Deploy to EC2') {
            steps {
                // This is a secure way to use your SSH key from Jenkins for test2
                sshagent(['ec2-key']) {
                    // This command copies all files from Jenkins to the Nginx webroot on your EC2 instance.
                    sh 'scp -r ./* ubuntu@54.253.26.102:/var/www/html/'
                }
            }
        }
    }
}