node {
   script {
      def props = readProperties file: "jenkinsfile.properties"

      def distribution= props['distribution_property'] 
      def tag= props['tag_property']

      properties([
         parameters([ 
            string(name: 'distribution', defaultValue: "$distribution", description: 'apt distribution'),
            string(name: 'tag', defaultValue: "$tag", description: 'just a tag'),
            choice(name: 'gradle_log_level', defaultValue: "$gradle_log_level", choices: ['quiet', 'warn', 'info', 'debug'].join('\n'), description: 'quiet || warn || info || debug')
         ])
      ])

         echo "distribution: ${params.distribution}"
         echo "tag: ${params.tag}"
   }
}

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}

