pipeline {
             agent {
        label "kubernetes"
               }  
    stages {         
        stage('Deployment') {
               steps {
                 			  script {
                            if ((BRANCH_NAME ==~ /(PROD)/)){
                    container('helm') {  
          withCredentials([file(credentialsId: 'KUBECONFIG', variable: 'KUBECONFIG')]) {
          sh '''
          export KUBECONFIG=$KUBECONFIG
          helm install nginx bitnami/nginx --namespace prod
          '''
        }
        }
}
                            if ((BRANCH_NAME ==~ /(STAGE)/)){
                    container('helm') {  
          withCredentials([file(credentialsId: 'KUBECONFIG', variable: 'KUBECONFIG')]) {
          sh '''
          export KUBECONFIG=$KUBECONFIG
          helm install nginx bitnami/nginx --namespace stage 
          '''
        }
        }
}
}
} 
}
    }
}
