node{
  stage('prep'){
    echo "hello"
  }
  stage('clone'){
    checkout scm
  }
  stage('Composer'){
    sh "composer install"
  }
  stage ('test'){
    echo "Testing"
  }
   stage ('Build'){
    sh "bin/magento setup:di:compile"
  }
  
   stage ('Deploy'){
    sh "bin/magento setup:static-content:deploy -f"
  }
  
   stage ('Maintain'){
    sh "bin/magento maintenance:enable"
  }
    
}
