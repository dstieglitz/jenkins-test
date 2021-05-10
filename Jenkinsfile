def props
def VERSION
def FIX
def RELEASE

node {
   props = readProperties file:"${BRANCH_NAME}.properties"
   VERSION = props['version']
}


pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                echo "${VERSION}"
            }
        }
    }
}

