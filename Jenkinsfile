pipeline {
    
   
   
    environment {
       //BUILD_NUMBER = "${env.BUILD_NUMBER}"
       BUILD_NUMBER = "latest"
       Workspace = "${env.WORKSPACE}"
       AKS_CLUSTER_NAME = 'commercialdev'
       AKS_RESOURCE_GROUP = 'AZ-CI-RG-DEV-CommercialSite-01'
       Tenantid = '7b17acfb-7376-4d68-8966-dc36cee137df'
       Password = 'uAv8Q~A_QMmzH.T.vGjiYcywbKnkXFo_G3DJwcmC'
       Appid = 'c1bf0699-8b61-4f5d-ae1e-4fbb6dafd905'
       
    }
    stages {
        
        stage('Checkout') {
            steps {
                 git branch: 'main', credentialsId: 'test', url: 'https://github.com/Abhi37-AGL/cicdtest.git'
            }
        }
 

   stage ('Build code and Push')
        {
            steps {
                script {
                    
                    
                       
                       def acrLoginServer = "commercialdev.azurecr.io"
                       def acrId = "commercialdev"
                       def acrPassword = "0q1R8urB/L3JyoMHt8Rf76HbyTQZSa1hTvbzhK3LEo+ACRDu2BL0"
                       sh "docker login ${acrLoginServer} -u ${acrId} -p ${acrPassword}"
                       WEB_IMAGE_NAME="${acrLoginServer}/azure-vote-front:kube${BUILD_NUMBER}"
                       sh "docker push $WEB_IMAGE_NAME"
                       }
                     }
         }
 }
}
