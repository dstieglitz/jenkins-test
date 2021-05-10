def distribution
def VERSION
def tag
def gradle_log_level
def defaults

node {
   all_defaults = readProperties file: 'jenkinsfile.properties'
   branch_defaults = readProperties file:"${BRANCH_NAME}.properties"
   VERSION = branch_defaults['version']
   distribution = all_defaults['distribution_property']
   tag = all_defaults['tag_property']
   gradle_log_level = all_defaults['gradle_log_level']
   defaults = [:]
   defaults.putAll(all_defaults)
   defaults.putAll(branch_defaults)
   println defaults
}

properties([
   parameters([ 
      string(name: 'distribution', defaultValue: "$distribution", description: 'apt distribution'),
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
    }
}

