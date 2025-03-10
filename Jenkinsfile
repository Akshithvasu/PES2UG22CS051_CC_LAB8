pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                    sh 'git branch -r'  // Debugging step to check available branches
                }
            }
        }

        stage('Setup Repository') {
            steps {
                script {
                    sh '''
                        git config --global user.email "akshithvasu333@gmail.com"
                        git config --global user.name "Jenkins"

                        # Ensure we are on the correct branch
                        git checkout main || git checkout -b main
                        
                        # Create the C++ file
                        echo '#include <iostream>' > PES2UG22CS051-1.cpp
                        echo 'using namespace std;' >> PES2UG22CS051-1.cpp
                        echo 'int main() {' >> PES2UG22CS051-1.cpp
                        echo '    cout << "Hello, Jenkins Pipeline!" << endl;' >> PES2UG22CS051-1.cpp
                        echo '    return 0;' >> PES2UG22CS051-1.cpp
                        echo '}' >> PES2UG22CS051-1.cpp
                        
                        git add PES2UG22CS051-1.cpp
                        git commit -m "Added C++ file PES2UG22CS051-1.cpp"
                        git push origin main
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Intentional error: Trying to compile a non-existing file
                    sh 'g++ nonexistentfile.cpp -o output'
                    sh './output'
                }
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
