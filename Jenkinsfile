node {
    def app

    stage('Clone repository') {
        /* Clone repository to our workspace */

        checkout scm
    }
    
    stage ('Deploy Policy') {
        /* Deploy runtime policy */
        withCredentials([usernameColonPassword(credentialsId: 'aquaui', variable: 'aquauipass')]) {
            sh "curl -H 'Content-Type: application/json' -X PUT -u $aquauipass -d @scb-demo-policy.json http://a84d335a29f2a11eaa485025822714ea-958075476.ap-southeast-1.elb.amazonaws.com:8080/api/v2/runtime_policies/scb-demo-policy"
        }
    }
    stage ('Validate Policy') {
        /* Deploy runtime policy */
        withCredentials([usernameColonPassword(credentialsId: 'aquaui', variable: 'aquauipass')]) {
            sh "curl -H 'Content-Type: application/json' -X GET -u $aquauipass http://a84d335a29f2a11eaa485025822714ea-958075476.ap-southeast-1.elb.amazonaws.com:8080/api/v2/runtime_policies/scb-demo-policy | jq"
        }
    }    
}
