def props
def VERSION
def FIX
def RELEASE

node {
   props = readProperties file:'jenkinsfile.properties'
   VERSION = props['distribution_property']
   FIX = props['tag_property']
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

