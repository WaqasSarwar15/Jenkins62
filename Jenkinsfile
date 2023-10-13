pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                echo "Maven Automate Build Started!!"
                echo "Maven Automate Build Completed!"
                
            }
        }
        stage("UnitTest"){
            steps{
                sh 'echo "artifact file" > unit_log.txt'
                echo "Unit Testing using JUNIT Started!"
                echo "Unit Testing using JUNIT Completed!"
            }
            post{
                success{
                    archiveArtifacts artifacts: 'unit_log.txt', onlyIfSuccessful: true
                        emailext attachLog: true, attachmentsPattern: 'generatedFile.txt', to: "waqassarwar15@yahoo.com",
                        subject: "Test Status",
                        body: "Unit Test was successful!"
                }
                failure{
                         archiveArtifacts artifacts: 'unit_log.txt', onlyIfSuccessful: true
                        emailext attachLog: true, attachmentsPattern: 'generatedFile.txt', to: "waqassarwar15@yahoo.com",
                        subject: "Test Status",
                        body: "Unit Test was failed!"
                    
                }
            }
        }
        stage("CodeAnalysis"){
            steps{
                echo "SonarQube Code Analysis Started!"
                echo "SonarQube Code Analysis Completed!"
            }
        }
        stage("SecurityScan"){
            steps{
                echo "SonarQube Security Scan Started!"
                echo "SonarQube Security Scan Completed!"
            }
            post{
                success{
                        mail to: "waqassarwar15@yahoo.com",
                        subject: "Security Scan Status",
                        body: "Security Scan was successful!"
                }
                failure{
                        mail to: "waqassarwar15@yahoo.com",
                        subject: "Security Scan Status",
                        body: "Security Scan was failed!"
                }
            }
        }
        stage("DeployStaging"){
            steps{
                echo "Deployment to AWS Staging Instance Started!"
                echo "Deployment to AWS Staging Instance Completed!"
            }
        }
        stage("IntegrationTests"){
            steps{
                echo "Integration Test using JUNIT Started!"
                echo "Integration Test using JUNITCompleted!"
            }
        }
        stage("DeployProduction"){
            steps{
                echo "Deployment to AWS Production Instance Started!"
                echo "Deployment to AWS Production Instance Completed!"
            }
        }
    }
}
