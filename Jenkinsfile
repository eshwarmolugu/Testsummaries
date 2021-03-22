pipeline {
  agent any
  tools {
    maven "Maven"
  }
  stages {
      stage("build") {
          steps {
            echo 'build..'
              snDevOpsStep()
            sleep 2
            snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "devops_pipeline_demo.jar","version": "1.0","semanticVersion": "1.0.0","repositoryName": "devops_pipeline_demo"}],"stageName": "build"}""")
              //sh 'mvn clean install'
            //snDevOpsChange()
          }
      }

      stage("test") {
           steps {
             echo 'test.'
                snDevOpsStep()
             sleep 2
                //sh 'mvn clean test -Dtest="unittests.*" -Dpublish'
                //junit '**/target/surefire-reports/*.xml'
             //sleep 2
             //sh 'mvn clean test -Dtest="ppmtests.*" -Dpublish'
               // junit '**/target/surefire-reports/*.xml'
             
             
           }
       }
      stage("deploy") {
          steps {
            echo 'Deploying.'
            snDevOpsStep()
            //snDevOpsArtifact(artifactsPayload:"""{"artifacts": [{"name": "devops_pipeline_demo.jar","version": "1.3","semanticVersion": "1.3.0","repositoryName": "devops_pipeline_demo"}],"stageName": "deploy"}""")
          	snDevOpsPackage(name: "devops_pipeline_demo", artifactsPayload: """{"artifacts": [{"name": "devops_pipeline_demo.jar","version": "1.0","semanticVersion": "1.0.0","repositoryName": "devops_pipeline_demo"}]}""")            
            sleep 5
            snDevOpsChange()
          }
      }
  }
}
