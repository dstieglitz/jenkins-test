import groovy.json.JsonSlurper

def distribution
def VERSION
def tag
def gradle_log_level
def defaults

node {
    all_defaults = readProperties file: 'jenkinsfile.properties'
    branch_defaults = readProperties file: "${BRANCH_NAME}.properties"
    subdir = readProperties file: "sub/sub.properties"
    VERSION = branch_defaults['version']
    distribution = all_defaults['distribution_property']
    tag = all_defaults['tag_property']
    gradle_log_level = all_defaults['gradle_log_level']
    defaults = [:]
    defaults.putAll(all_defaults)
    defaults.putAll(branch_defaults)
    defaults.putAll(subdir)
    println defaults
}

properties([
        parameters([
                string(name: 'distribution', defaultValue: defaults['DOES_NOT_EXIST'], description: 'apt distribution'),
                string(name: 'tag', defaultValue: "$tag", description: 'just a tag'),
                choice(name: 'gradle_log_level', defaultValue: "$gradle_log_level", choices: ['quiet', 'warn', 'info', 'debug'].join('\n'), description: 'quiet || warn || info || debug')
        ])
])


pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                echo "${VERSION}"
            }
        }
//       stage('Test HTTP Request') {
//          steps {
//             script {
//                 def response = httpRequest 'https://dog.ceo/api/breeds/list/all'
//
//                def patchOrg = """
//                  {"description": "$description"}
//                """
//                
//                def response = httpRequest acceptType: 'APPLICATION_JSON', 
//                    contentType: 'APPLICATION_JSON', 
//                    httpMode: 'POST', 
//                    requestBody: patchOrg, 
//                    url: "https://api.github.com/orgs/${orgName}"
//  
//                 def json = new JsonSlurper().parseText(response.content)
//
//                 echo "Status: ${response.status}"
//
//                 echo "Dogs: ${json.message.keySet()}"
//             }
//          }
//       }
//    }
    }
    post {
        always {
            script {
                currentBuild.description = "version=${BUILD_NUMBER}"
            }
        }
    }
}

