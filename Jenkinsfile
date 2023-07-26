pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Checkout from Github'
                git branch: 'main', credentialsId: 'GitHub-User', url: 'https://github.com/neerajdubey2023/Simple-Ant-job'
            }
        }
        stage('Accessing api from external server'){
            steps{
                echo 'in step2'
                println "The groovy runtime version is $GroovySystem.version"
                script{
                    def getURL = new URL('http://localhost:1100/rest-api/customers/1')
                    def connection = getURL.openConnection()
                    connection.requestMethod = 'GET'
                    connection.setRequestProperty("Accept", "application/json");

                    assert connection.responseCode == 200
                
                    BufferedReader reader = new BufferedReader(new InputStreamReader(connection.getInputStream()));

                   println("\nThe JSON format of customer sent by rest-server...\n");

                    line = reader.readLine();
                    def res =line

                     while (line != null) {
            	       println(line);
	
	                    line = reader.readLine();
                    }
                    connection.disconnect();
                 }

            }
        }
    }
}
