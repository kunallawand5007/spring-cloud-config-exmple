when we devloping microservice based architecture you may face cross cutting concern for  property file 

A service typically calls other services and databases as well. 
For each environment like dev, QA, UAT, prod, the endpoint URL or some configuration properties might be different

we can these promblem with 2 approch

1. External property file Configuration
 
  In this if we chnaged any prperty or added or updated any value we need to restart the microservice 
  we need to passed property file while runnng jar file 
  ex.> java -jar a.jar -Dloader.path=file://path to comman property file.     
	 
 
2. Used Spring cloud config server
   In this case we used  
   Spring Cloud config server provides the option to externalize the properties  	
   These can be accessed by the application on startup or can be refreshed without a server restart.	   
		 

spring-cloud-config-exmple

This sample example for showing how to used spring cloud config server for externalized property files for different envirnoment


Test property chnages :

1. open browser hit URl:http://localhost:8081/read/property

output will you see the value from propery file


Make some change, in the value of the property in the config-server-client-development.properties and check-in in the local git, then hit the http://localhost:8081/read/property again in the browser, You will the old value only.

To reflect the new value, we need to refresh the configuration by hitting http://localhost:8081/refresh endpoint using POST method from any of the REST client.

We have addded @RefreshScope annotation the Rest Controller that we refresh client service
   

