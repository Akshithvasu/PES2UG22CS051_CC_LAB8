pipeline {
    agent any

    stages {
        stage('Setup Repository') {
            steps {
                script {
                    sh '''
                    git config --global user.email "akshithvasu333@gmail.com"
                    git config --global user.name "Jenkins"

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
                    sh 'g++ -o PES2UG22CS051-1 PES2UG22CS051-1.cpp'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS051-1'
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
