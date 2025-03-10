pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Setup Repository') {
            steps {
                script {
                    sh '''
                        git config --global user.email "akshithvasu333@gmail.com"
                        git config --global user.name "Jenkins"

                        # Checkout the main branch (or create if it doesn’t exist)
                        git checkout main || git checkout -b main

                        # Modify the file to ensure a new commit (avoids "nothing to commit" issue)
                        echo "// Modified file for Jenkins test" >> PES2UG22CS051-1.cpp

                        git add PES2UG22CS051-1.cpp
                        git commit -m "Updated C++ file to trigger build"
                        git push origin main
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh '''
                        # Compile the C++ program
                        g++ PES2UG22CS051-1.cpp -o output

                        # Run the compiled program
                        ./output
                    '''
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline failed"
        }
    }
}
