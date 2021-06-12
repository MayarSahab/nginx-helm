pipeline {
             agent {
        label "kubernetes"
               }  
    stages {         
        stage('Dev Deployment') {
               steps {
                    container('helm') {  
          withCredentials([file(credentialsId: 'KUBECONFIG', variable: 'KUBECONFIG')]) {
          sh '''
          export KUBECONFIG=$KUBECONFIG
          helm install nginx bitnami/nginx --namespace dev
          '''
        }
        }
}
}
       stage('Stage Deployment') {
               steps {
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
