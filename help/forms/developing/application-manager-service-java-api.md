---
title: Application Manager Service JavaAPI Quick Start(SOAP)
seo-title: Application Manager Service JavaAPI Quick Start(SOAP)
description: null
seo-description: null
uuid: ce26f3bc-8250-483a-a4b6-91ebdb45c584
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 2c7bd405-c4e9-4e3b-9ef7-aa6d931c30a7
---

# Application Manager Service JavaAPI Quick Start(SOAP){#application-manager-service-javaapi-quick-start-soap}

Java API Quick Start(SOAP) is available for the Application Manager service.

[Quick Start: Deploying applications using the Java API(SOAP)](application-manager-service-java-api#quick_start_soap_mode_deploying_applications_using_the_java_api)

[Quick Start: Removing an application using the Java API(SOAP)](application-manager-service-java-api#quick_start_soap_mode_removing_an_application_using_the_java_api)

>[!NOTE]
>
>The application manager APIs support only AEM Forms LCA files. It does not support LCA files of LiveCycle ES2 and ES4.

AEM Forms operations can be performed using the AEM Forms strongly typed API and the connection mode should be set to SOAP.

*

## Quick Start (SOAP mode): Deploying Applications using the Java API {#quick-start-soap-mode-deploying-applications-using-the-java-api}

The following Java code example imports an application based on an existing LCA file named *EncryptDocument.lca*. (See [Deploying applications](/programming-with-aem-forms/processes-tasks#deploying_applications).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
    * 3. activation.jar (required for SOAP mode) 
    * 4. axis.jar (required for SOAP mode) 
    * 5. commons-codec-1.3.jar (required for SOAP mode) 
    * 6. commons-collections-3.2.jar  (required for SOAP mode) 
    * 7. commons-discovery.jar (required for SOAP mode) 
    * 8. commons-logging.jar (required for SOAP mode) 
    * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 11. jaxrpc.jar (required for SOAP mode) 
    * 12. log4j.jar (required for SOAP mode) 
    * 13. mail.jar (required for SOAP mode) 
    * 14. saaj.jar (required for SOAP mode) 
    * 15. wsdl4j.jar (required for SOAP mode) 
    * 16. xalan.jar (required for SOAP mode) 
    * 17. xbean.jar (required for SOAP mode) 
    * 18. xercesImpl.jar (required for SOAP mode) 
     * 19. adobe-workflow-client-sdk.jar 
     * 20. adobe-applicationmanager-client-sdk.jar 
      
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
  
 import java.io.FileInputStream; 
 import java.util.*; 
  
 import com.adobe.idp.Document; 
 import com.adobe.idp.applicationmanager.application.ApplicationStatus; 
 import com.adobe.idp.applicationmanager.client.ApplicationManager; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class DeployApplication { 
  
     public static void main(String[] args) { 
      
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
              
             //Get the AEM Forms application to deploy  
             FileInputStream fileApp = new FileInputStream("C:\\Adobe\EncryptDocument.lca"); 
             Document lcApp = new Document(fileApp); 
                                  
             //Create an ApplicationManager object 
             ApplicationManager appManager = new ApplicationManager(myFactory);  
              
             //Import the application into the production server 
             ApplicationStatus appStatus = appManager.importApplicationArchive(lcApp); 
             int status = appStatus.getStatusCode(); 
              
             //Determine if the application was successfully deployed 
             if (status==1) 
                     System.out.println("The application was successfully deployed"); 
             else 
                     System.out.println("The application was not successfully deployed. The status is "+status); 
         } 
         catch(Exception e) 
         { 
             e.printStackTrace(); 
         } 
     } 
 } 
 
```

## Quick Start (SOAP mode): Removing an application using the Java API {#quick-start-soap-mode-removing-an-application-using-the-java-api}

The following Java code example removes an application named *EncryptDocument*. (See [Removing Applications](/programming-with-aem-forms/processes-tasks#removing_applications).)

```as3
 /* 
     * This Java Quick Start uses the SOAP mode and contains the following JAR files 
     * in the class path: 
     * 1. adobe-livecycle-client.jar 
     * 2. adobe-usermanager-client.jar 
    * 3. activation.jar (required for SOAP mode) 
    * 4. axis.jar (required for SOAP mode) 
    * 5. commons-codec-1.3.jar (required for SOAP mode) 
    * 6. commons-collections-3.2.jar  (required for SOAP mode) 
    * 7. commons-discovery.jar (required for SOAP mode) 
    * 8. commons-logging.jar (required for SOAP mode) 
    * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode) 
    * 10. jaxen-1.1-beta-9.jar (required for SOAP mode) 
    * 11. jaxrpc.jar (required for SOAP mode) 
    * 12. log4j.jar (required for SOAP mode) 
    * 13. mail.jar (required for SOAP mode) 
    * 14. saaj.jar (required for SOAP mode) 
    * 15. wsdl4j.jar (required for SOAP mode) 
    * 16. xalan.jar (required for SOAP mode) 
    * 17. xbean.jar (required for SOAP mode) 
    * 18. xercesImpl.jar (required for SOAP mode) 
     * 19. adobe-workflow-client-sdk.jar 
     * 20. adobe-applicationmanager-client-sdk.jar 
     * 
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to  
     * your local development environment and then include the 3 JBoss JAR files in your class path 
     * 
     * These JAR files are located in the following path: 
     * <install directory>/sdk/client-libs/common 
     * 
     * 
     * <install directory>/jboss/bin/client 
     * 
     * If you want to invoke a remote forms server instance and there is a 
     * firewall between the client application and the server, then it is  
     * recommended that you use the SOAP mode. When using the SOAP mode,  
     * you have to include additional JAR files located in the following  
     * path 
     * <install directory>/sdk/client-libs/thirdparty 
     * 
     * For information about the SOAP  
     * mode and the additional JAR files that need to be included,  
     * see "Setting connection properties" in Programming  
     * with AEM Forms 
     */ 
  
  
 import java.util.*; 
  
 import com.adobe.idp.applicationmanager.application.Application; 
 import com.adobe.idp.applicationmanager.application.ApplicationId; 
  
 import com.adobe.idp.applicationmanager.client.ApplicationManager; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties; 
  
 public class RemoveApplication { 
  
     public static void main(String[] args) { 
          
          
         try{ 
             //Set connection properties required to invoke AEM Forms                                 
             Properties connectionProps = new Properties(); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://[server]:[port]"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);           
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator"); 
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password"); 
              
             //Create a ServiceClientFactory object 
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps); 
  
             //Create a ComponentRegistryClient object 
             ApplicationManager appManager = new ApplicationManager(myFactory);  
                                  
             //Get all the deployed applications 
             List allApps = appManager.getApplications(); 
                      
             //Iterate through the applications 
             Iterator iter= allApps.iterator(); 
             while (iter.hasNext()) { 
                          
              //Cast each element to an Application object 
              Application myApplication  = (Application)iter.next();     
              ApplicationId appID = myApplication.getApplicationId(); 
              String appName = appID.getApplicationName(); 
                           
              System.out.println("The name of the AEM Forms application is "+ appID.getApplicationName());  
              //Determine the name of the application 
              if (appName.compareTo("EncryptDocument")==0) 
              { 
                  //Remove the application 
                 appManager.removeApplication(appID); 
                 System.out.println("The  "+ appID.getApplicationName() +" application was removed."); 
              } 
         } 
         } 
         catch(Exception e) 
             { 
             e.printStackTrace(); 
             } 
     } 
 } 
 
```
