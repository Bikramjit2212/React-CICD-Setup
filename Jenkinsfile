pipeline {
    agent any
    options {
        skipDefaultCheckout(true) // We will manual checkout or use clean checkout
    }
    stages {
        stage('Cleanup Code') {
            steps {
                cleanWs()
            }
        }

        stage('Checkout Using SCM'){
            steps{
                checkout scm // Now we download the code AFTER cleaning
            }
        }

        stage('Build'){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true //reuse node for next steps
                    // Running as root prevents the EACCES permission errors 
                    // when npm tries to create the /.npm cache directory
                    args '-u root' //so that it uses as the root user
                }
            }

            steps {
                //running shell script
                sh '''
                    echo "Current User: $(whoami)"
                    node --version
                    npm --version
                    
                    # Clean previous builds if they exist to avoid conflicts
                    rm -rf node_modules dist
                    
                    # Install dependencies
                    # --legacy-peer-deps handles the React 18/19 version conflicts seen in your logs
                    npm install --legacy-peer-deps
                    
                    # Run the build
                    npm run build
                    
                    ls -l
                '''
            }
        }
    }
}