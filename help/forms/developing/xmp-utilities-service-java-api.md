---
title: Démarrage rapide de l’API Java du service XMP Utilities (SOAP)
description: Utilisez le service XMP Utilities pour exporter et importer des métadonnées XMP.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations,AEM Forms on JEE
hide: true
hidefromtoc: true
exl-id: 6c2bdfc3-0f7b-4d53-b17e-f4cd11ab40ea
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 100%

---

# Démarrage rapide de l’API Java du service XMP Utilities (SOAP) {#xmp-utilities-service-java-apiquick-start-soap}

Les démarrages rapides suivants sont disponibles pour le service XMP Utilities.

[Démarrage rapide (mode SOAP) : exporter des métadonnées XMP à l’aide de l’API Java](xmp-utilities-service-java-api.md#quick-start-soap-mode-exporting-xmp-metadata-using-the-java-api)

[Démarrage rapide (mode SOAP) : importer des métadonnées XMP à l’aide de l’API Java](xmp-utilities-service-java-api.md#quick-start-soap-mode-importing-xmp-metadata-using-the-java-api)

Les opérations AEM Forms peuvent être effectuées à l’aide de l’API fortement typée dʼAEM Forms et le mode de connexion doit être défini sur SOAP.

>[!NOTE]
>
>Les démarrages rapides dans Programmation avec AEM Forms sont basés sur le serveur Forms. Si vous utilisez un autre système d’exploitation, tel qu’UNIX, remplacez les chemins spécifiques à Windows par les chemins pris en charge par le système d’exploitation approprié. De même, si vous utilisez un autre serveur d’applications J2EE, veillez à spécifier des propriétés de connexion valides. Voir [Réglage des propriétés de la connexion](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Démarrage rapide (mode SOAP) : exporter des métadonnées XMP à l’aide de l’API Java {#quick-start-soap-mode-exporting-xmp-metadata-using-the-java-api}

L’exemple de code suivant permet de récupérer les métadonnées XMP, de les inspecter et de les enregistrer. (Consultez la section [Exporter des métadonnées à partir de documents PDF](/help/forms/developing/xmp-utilities.md#exporting-metadata-from-pdf-documents)).

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-pdfutility-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     *
     * For complete details about the location of the AEM Forms JAR files,
     * see "Including AEM Forms Java library files" in Programming
     * with AEM Forms
     */
 import com.adobe.livecycle.xmputility.*;
 import com.adobe.livecycle.xmputility.client.*;
 import java.util.*;
 import java.io.*;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 public class ExportMetadata
 {
     public static void main(String[] args)
     {
         try
         {
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory instance
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
 
             // Create a XMP Utility client
             XMPUtilityServiceClient xmpUt = new XMPUtilityServiceClient(factory);
 
             // Specify a PDF document whose metadata is to be exported
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.pdf");
             Document inDoc = new Document(fileInputStream);
 
             // Export the XMP metadata object
             XMPUtilityMetadata myXmp = xmpUt.exportMetadata(inDoc);
 
             // Inspect the XMP metadata object (retrieve the document?s author in this case)
             String name = myXmp.getAuthor();
             System.out.println("The document?s author is " + name);
 
             // Export the XMP metadata to an XML file
             Document outDoc = xmpUt.exportXMP(inDoc);
             File xmpFile = new File("c:\\LoanMetaData.xml");
             outDoc.copyToFile(xmpFile);
         }
         catch (Exception e)
         {
             System.out.println("Error occurred: " + e.getMessage());
         }
     }
 }
 
```

## Démarrage rapide (mode SOAP) : importer des métadonnées XMP à l’aide de l’API Java {#quick-start-soap-mode-importing-xmp-metadata-using-the-java-api}

L’exemple de code suivant permet dʼimporter des métadonnées XMP et dʼenregistrer le nouveau fichier PDF sur le disque. Le document PDF est basé sur un fichier PDF nommé Loan.pdf. Le document XML contenant les métadonnées à importer dans le document PDF est basé sur un fichier XML nommé *LoanMetaData.xml*. Pour plus d’informations sur ce fichier XML, consultez la section [Importer des métadonnées dans des documents PDF](/help/forms/developing/xmp-utilities.md#importing-metadata-into-pdf-documents).

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-pdfutility-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     *
     * For complete details about the location of the AEM Forms JAR files,
     * see "Including AEM Forms Java library files" in Programming
     * with AEM Forms
     */
 import com.adobe.livecycle.xmputility.*;
 import com.adobe.livecycle.xmputility.client.*;
 import java.util.*;
 import java.io.*;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 public class ImportMetadata
 {
     public static void main(String[] args)
     {
         try
         {
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory instance
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a XMP Utility client
             XMPUtilityServiceClient xmpUt = new XMPUtilityServiceClient(factory);
 
             //Specify a PDF document into which XMP metadata is imported
             FileInputStream filePDF = new FileInputStream("C:\\Adobe\Loan.pdf");
             Document inDoc = new Document(filePDF);
 
             //Specify an XML file containing XMP metadata to import
             FileInputStream fileXML = new FileInputStream("C:\\Adobe\LoanMetaData.xml");
             Document xmpDoc = new Document(fileXML );
 
             //Import the XMP metadata
             Document outDoc = xmpUt.importXMP(inDoc, xmpDoc);
 
             //Inspect the XMP metadata object (retrieve the document?s author in this case)
             XMPUtilityMetadata myXmp = xmpUt.exportMetadata(outDoc);
             String name = myXmp.getAuthor();
             System.out.println("The document?s author is " + name);
 
             //Save the PDF document containing the new metadata
             File pdfFile = new File("c:\\Adobe\LoanWithMetadata.pdf");
             outDoc.copyToFile(pdfFile);
         }
         catch (Exception e)
         {
             System.out.println("Error occurred: " + e.getMessage());
         }
     }
 }
```
