pipeline {
  agent any
  
  tools {
    jdk 'Java'
  }

  environment {
    JAVA_HOME = tool 'Java'
  }

  stages {
    stage('Checkout') {
        steps {
            git url: 'https://github.com/por314159ug/application-java.git', branch: 'main'
        }
    }

    stage('Compile') {
      steps {
        bat '"%JAVA_HOME%\\bin\\javac" -d build\\classes Main.java'
      }
    }
  }

}
