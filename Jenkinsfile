pipeline{
  agent any
  tools{
    maven 'maven'
  }
  stages{
    stage("Clean un"){
      steps{
        deleteDir()
      }
    }
    stage("Clone repo"){
      steps{
        sh "git clone https://github.com/MedAmineBS/TP-1-Cucumber-Sel-Jenkins.git "
      }
    }
    stage("Generate tests"){
      steps{
        dir("TP-1-Cucumber-Sel-Jenkins"){
          sh "mvn clean install "
          cucumber buildStatus: 'UNCHANGED', customCssFiles: '', customJsFiles: '', failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: '**/*.json', pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1
        }
      }
    }
    stage("Archive the result"){
      steps{
        dir("TP-1-Cucumber-Sel-Jenkins"){
          archiveArtifacts 'target/*.jar'
        }
      }
    }
  }
}