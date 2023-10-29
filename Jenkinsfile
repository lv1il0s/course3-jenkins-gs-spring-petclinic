pipeline {
    agent any
    stages {
        stage("checkout"){
            steps {
                git branch:'main', url: 'https://github.com/lv1il0s/course3-jenkins-gs-spring-petclinic'
            }
        }
        stage("build"){
            steps {
                sh "./mvnw package"
            }
        }
        stage("capture"){
            steps {
                archiveArtifacts artifacts: '**/target/*.jar'
                jacoco()
                junit '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
    //post {
        //regression - called only if current build is worse than previous (failure after success)
        //always {
            //emailext body: "${env.BUILD_URL}\n${currentBuild.absoluteUrl}",
            //to: 'some-email',
            //recepientProviders: [previous()],
            //subject: "${currentBuild.currentResult}: Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]"
        //}
    //}
    
}