# Hello World Rest API

### Running the Application

Run RestfulWebServicesApplication as a Java Application.

- http://localhost:8080/hello-world

```txt
Hello World
```

- http://localhost:8080/hello-world-bean

```json
{"message":"Hello World"}
```

- http://localhost:8080/hello-world/path-variable/santo

```json
{"message":"Hello World, in28minutes"}
```

### Plugin configuration

```
<plugin>
	<groupId>com.microsoft.azure</groupId>
	<artifactId>azure-webapp-maven-plugin</artifactId>
	<version>1.7.0</version>
</plugin>
```
				
### Azure CLI

- https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest

### Final Plugin Configuration
```
<plugin>
	<groupId>com.microsoft.azure</groupId>
	<artifactId>azure-webapp-maven-plugin</artifactId>
	<version>1.7.0</version>
	<configuration>
		<schemaVersion>V2</schemaVersion>
		<resourceGroup>hello-world-rest-api-rg</resourceGroup>
		<appName>hello-world-rest-api-in28minutes</appName>
		<pricingTier>B1</pricingTier>
		<region>westeurope</region>
		<appSettings>
			<property>
				<name>JAVA_OPTS</name>
				<value>-Dserver.port=80</value>
			</property>
		</appSettings>
		<runtime>
			<os>linux</os>
			<javaVersion>java11</javaVersion>
			<webContainer>java11</webContainer>
		</runtime>
		<deployment>
			<resources>
				<resource>
					<directory>${project.basedir}/target</directory>
					<includes>
						<include>*.jar</include>
					</includes>
				</resource>
			</resources>
		</deployment>
	</configuration>
</plugin>

```
### Logging Configuration

```
-Dlogging.level.org.springframework=DEBUG
```
---------------------------
- Update Maven settings.xml from User/.m2
- Get this information from  az login commmand
- Use Powershell for all commands
------------------------------------
```<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                          https://maven.apache.org/xsd/settings-1.0.0.xsd">
<servers>
	<server>
	    <id>azure-auth</id>
	    <configuration>
	        <client>2bdc7cc7-02ca-4c9e-aa54-eaae42347739</client>
	        <tenant>26d2b79a-fc49-4f9e-b131-c65bfaae1282</tenant>
	        <key>[password]</key>
	        <environment>AZURE</environment>
	    </configuration>
	</server>
</servers>
</settings>
```

- Download Azure CLI
- Verify installation: az --version
- az login
- add entire plugin definition into pom.xml 
   com.microsoft.azure
- azure-webapp:config  - Config project with Azure plugin
- azure-webapp:deploy  - Deploy application on Azure 

Homepage URL - 
https://santo-hello-world-rest-api.azurewebsites.net/hello-world

- Check log streams, first enable loggin from API service
 az webapp log tail --name santo-hello-world-rest-api[appName] --resource-group hello-world-rest-api-rg[resource-group]
