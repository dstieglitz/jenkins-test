def props
def VERSION
def FIX
def RELEASE

node {
   props = readProperties file:'jenkinsfile.properties'
   VERSION = props['version']
   FIX = props['fix']
   RELEASE = VERSION + "_" + FIX
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

