pipeline {
    agent any

    stages {
        stage('Setup Repository') {
            steps {
                script {
                    sh '''
                    echo '#include <iostream>' > PES2UG22CS051.cpp
                    echo 'using namespace std;' >> PES2UG22CS051.cpp
                    echo 'int main() {' >> PES2UG22CS051.cpp
                    echo '    cout << "Hello, Jenkins Pipeline!" << endl;' >> PES2UG22CS051.cpp
                    echo '    return 0;' >> PES2UG22CS051.cpp
                    echo '}' >> PES2UG22CS051.cpp
                    '''
                    sh 'git add PES2UG22CS051.cpp'
                    sh 'git commit -m "Added C++ file PES2UG22CS051.cpp"'
                    sh 'git push origin main'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'g++ -o PES2UG22CS051 PES2UG22CS051.cpp'
                    echo 'Build Stage Successful'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS051'
                    echo 'Test Stage Successful'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deployment Successful'
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
