pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Checks out the source code from your GitHub repo
            }
        }

        stage('S3 Upload') {
            steps {
                withAWS(region: 'us-east-1', credentials: 'f311f107-e92a-4f0d-b1d8-56da006d7a95') {
                    sh '''
                        # List contents to verify files are available
                        ls -la

                        # Upload the index.html file to the S3 bucket 
                        aws s3 cp index.html s3://
jenbucket01/

                        # Optionally, you can upload additional assets (like CSS, JS, etc.)
                        # aws s3 cp ./assets/ s3://
jenbucket01/assets/ --recursive
                    '''
                }
            }
        }
    }
}
