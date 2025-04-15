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

    stage('Prepare Manifest') {
      steps {
        bat '''
          if not exist build\\classes (
            mkdir build\\classes
          )
          echo Main-Class: Main > build\\classes\\manifest.txt
        '''
      }
    }

    stage('Package') {
      steps {
        bat '''
          if not exist build\\jar (
            mkdir build\\jar
          )
          "%JAVA_HOME%\\bin\\jar" cfm build\\jar\\MyApplication.jar build\\classes\\manifest.txt -C build\\classes .
        '''
      }
    }

    stage('Run') {
      steps {
        bat '"%JAVA_HOME%\\bin\\java" -jar build\\jar\\MyApplication.jar'
      }
    }
  }
}
