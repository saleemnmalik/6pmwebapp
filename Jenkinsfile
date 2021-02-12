node{
    
    def mvnHome = tool name: 'maven3', type: 'maven'
    
    stage('SCM Checkout'){
        
        git credentialsId: 'github', url: 'https://github.com/saleemnmalik/6pmwebapp'
    }
    
    stage('MVN Build'){
        
        sh "${mvnHome}/bin/mvn clean package"
        
    }
    
}
