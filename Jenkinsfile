node{
    
  stage('prep'){
    echo "hello"
  }

  stage ('Clean Cache'){
    sh"sudo php bin/magento cache:clean"
  }
     stage ('Upgrade'){
    sh "sudo bin/magento setup:upgrade"
  }
   stage ('Build'){
    sh "sudo bin/magento setup:di:compile"
  }
  
   stage ('Deploy'){
    sh "sudo php bin/magento setup:static-content:deploy en_US ar_SA --force"
    sh"sudo php bin/magento cache:clean"
    sh" sudo php bin/magento indexer:reindex"
  }
  
   stage ('Nginx'){
    sh" sudo chown -R www-data: ."
    sh" sudo chmod -R 775 ."
    sh" sudo service nginx restart"
   }
    
}
