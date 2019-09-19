
node {  
    stage('Code Checkout'){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/jeet1988/sqlscript']]])
    }
    stage('Copy'){
        bat "for %%I in (*.sql) do copy %%I D:\\tools\\flyway-5.2.3\\sql"
    }
    stage('Deploy') { 
        def flyway="D:\\tools\\flyway-5.2.3\\sql"
               echo "Deploying"
               bat "D:\\tools\\flyway-5.2.3\\flyway.cmd -user=root -password=root -url=jdbc:mysql://localhost:3306/FlyWayDB repair migrate validate info"
    }

}
