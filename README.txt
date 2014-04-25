Product: Integration tests for WSO2 ESB Confluence connector

Pre-requisites:

 - Maven 3.x
 - Java 1.6 or above

Tested Platform: 

 - Ubuntu 12.04
 - WSO2 ESB 4.8.1
		  
STEPS:
1. Make sure the ESB 4.8.1 zip file with latest patches available at "Integration_Test\products\esb\4.8.1\modules\distribution\target\".

2. This ESB should be configured as below;
	In Axis configurations (\repository\conf\axis2\axis2.xml).

   i) Enable message formatter for "text/html"
		<messageFormatters>
			<messageFormatter contentType="text/html" class="org.wso2.carbon.relay.ExpandingMessageFormatter"/>\
		</messageFormatters>

   ii) Enable message builder for "text/html"
		<messageBuilders>
			<messageBuilder contentType="text/html" class="org.wso2.carbon.relay.BinaryRelayBuilder"/>
		</messageBuilders>

2. Copy confluence connector zip file (paypal.zip) to the location "Integration_Test\products\esb\4.8.1\modules\integration\confluence_conect\repository\"

3. Make sure the confluence test suite is enabled (as given below) and all other test suites are commented in the following file - "Integration_Test\products\esb\4.8.1\modules\integration\connectors\src\test\resources\testng.xml"  
     <test name="Confluence-Connector-Test" preserve-order="true" verbose="2">
	<packages>

            <package name="org.wso2.carbon.connector.integration.test.confluence"/>

        </packages>
 
    </test>
4.Configure Atlassian confluence as bellow.
i)Change the username, password and uri for the confluence instance in confluence.properties file
ii)Enter invalid password in wrongPassword field.
iii)Enable backup and restore data from confluence.cfg.xml file
iv)Create and enable pluging name plugging1


6. Copy proxy files to location "Integration_Test\products\esb\4.8.1\modules\integration\connectors\src\test\resources\artifacts\ESB\config\proxies\confluence\"

7. Copy request files to location "Integration_Test\products\esb\4.8.1\modules\integration\connectors\src\test\resources\artifacts\ESB\config\soapRequest\confluence\" 

8. Navigate to "Integration_Test\products\esb\4.8.1\modules\integration\confluence_connect\" and run the following command.
     $ mvn clean install
