------------------------------------------------------------------------------------------------------------------
# Web Application to deploy on Azure
- ----------------------------------------------------------
@@This application doesn't have embedded tomcat(SpringBootServletInitializer implemented) and output package is WAR@@
## Run Application using maven Goal :   spring-boot:run
    URL -   http://localhost:8080/login with santo/dummy as credentials
------------------------------------------------------------------------------------------------------------------
## H2 Console
   - http://localhost:8080/h2-console
   - Use `jdbc:h2:mem:testdb` as JDBC URL 
    H2  -   http://localhost:8080/h2-console
            jdbc:h2:mem:testdb
     Create WAR package : mvn clean install 
------------------------------------------------------------------------------------------------------------------
## Azure deployment
    Powershell cd to pom.xml path : Command prompt may cause an error
    - Add following plugin details 
        <plugin>
        	<groupId>com.microsoft.azure</groupId>
        	<artifactId>azure-webapp-maven-plugin</artifactId>
        	<version>1.7.0</version>
        </plugin>
        
    -  mvn azure-webapp:config
        - pom.xml will be udpated. Change the appname and resource group as expected
        - to update the configuration re-run the command
    -  mvn azure-webapp:deploy 
        - Copy the URL -  https://azure-basic-webapp-deployment-ii.azurewebsites.net/login
        - H2 Cosole    - https://azure-basic-webapp-deployment-ii.azurewebsites.net/h2-console
------------------------------------------------------------------------------------------------------------------
