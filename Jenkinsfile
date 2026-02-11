pipeline {
    agent any

    environment {
        MY_VAR = 'my value'
        VERCEL_TOKEN = credentials('VERCEL_TOKEN')
    }
    options {
        skipDefaultCheckout(true) // We will manual checkout or use clean checkout so skip the default checkout
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
                    image 'node:22.11.0-alpine3.20'
                    args '-u root' //so that it uses as the root user
                    reuseNode true //reuse node for next steps
                    // Running as root prevents the EACCES permission errors 
                    // when npm tries to create the /.npm cache directory 
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
                    npm install 
                    
                    # Run the build
                    npm run build
                    
                    ls -l
                '''
            }
        }

        stage('Test'){
            agent {
                docker {
                    image 'node:22.11.0-alpine3.20'
                    args '-u root'
                    reuseNode true
                    
                }
            }
            steps {
                sh'''
                    npm run test
                    test -f dist/index.html
                '''
            }
        }

        stage('Deploy'){
            agent {
                docker {
                    image 'node:22.11.0-alpine3.20'
                    args '-u root'
                    reuseNode true
                }
            }
            steps {
                //install vercel as global dependency
                sh '''
                    npm install -g vercel 
                    echo $MY_VAR
                    vercel --prod --token=$VERCEL_TOKEN --confirm --name=cicd_project
                '''
            }
        }
    }
}