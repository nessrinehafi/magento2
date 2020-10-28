node{
    
    deleteDir()
  stage('prep'){
    echo "hello"
  }
  stage('clone'){
    checkout scm
  }
  stage('Composer'){
    sh "composer update"
  }
  stage ('Clean Cache'){
    sh"php bin/magento cache:clean"
  }
     stage ('Upgrade'){
    sh "bin/magento setup:upgrade"
  }
   stage ('Build'){
    sh "bin/magento setup:di:compile"
  }
  
   stage ('Deploy'){
    sh "php bin/magento setup:static-content:deploy en_US ar_SA --force"
    sh"php bin/magento cache:clean"
    sh" php bin/magento indexer:reindex"
  }
  
   stage ('Nginx'){
    sh" sudo chown -R www-data: ."
    sh" sudo chmod -R 775 ."
    sh" sudo service nginx restart"
   }
    
}
