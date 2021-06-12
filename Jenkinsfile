pipeline {
             agent {
        label "kubernetes"
               }  
    stages {         
        stage('Dev Deployment') {
               steps {
                 			  script {
                            if ((BRANCH_NAME ==~ /(DEV)/)){
                    container('helm') {  
          withCredentials([file(credentialsId: 'KUBECONFIG', variable: 'KUBECONFIG')]) {
          sh '''
          export KUBECONFIG=$KUBECONFIG
          helm install nginx bitnami/nginx --namespace dev
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
