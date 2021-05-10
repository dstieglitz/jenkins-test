def props
def VERSION
def FIX
def RELEASE

node {
   println "BRANCH_NAME=${BRANCH_NAME}"
   props = readProperties file:"${BRANCH_NAME}.properties"
   println props
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

