---
title: "D&#233;pannage des exceptions&#160;: System.ServiceModel.Security.MessageSecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.ServiceModel.Security.MessageSecurityException (exception)"
  - "MessageSecurityException (exception)"
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.ServiceModel.Security.MessageSecurityException
Une exception <xref:System.ServiceModel.Security.MessageSecurityException> est renvoyée lorsque [!INCLUDE[vsindigo](../misc/includes/vsindigo_md.md)] détermine qu'un message n'est pas correctement sécurisé ou qu'il a été falsifié. L'erreur se produit le plus fréquemment lorsque les conditions suivantes se vérifient toutes :  
  
-   Vous utilisez une référence de service WCF via une connexion à distance telle qu'une connexion bureau à distance ou Terminal Services pour communiquer avec un service WCF \(.svc\) dans un projet de site Web ou d'application Web.  
  
-   Vous ne possédez pas des autorisations d'administrateur sur le site distant.  
  
-   Les demandes adressées à localhost sur le site distant sont gérées par le serveur de développement [!INCLUDE[vstecasp](../misc/includes/vstecasp_md.md)].  
  
## Conseils associés  
 **Résoudre les problèmes d'authentification NTLM lors de l'utilisation du serveur de développement ASP.NET.**  
 La sécurité de Stimulation\/Réponse de Windows NT \(NTLM\) est généralement désactivée sur le serveur de développement [!INCLUDE[vstecasp](../misc/includes/vstecasp_md.md)], ce qui permet l'accès anonyme. Par défaut, lorsque vous exécutez une session Terminal Services ou utilisez une connexion à distance, la sécurité NTLM est activée. Lorsque NTLM est activé, toutes les demandes adressées à localhost sont validées par rapport aux informations d'identification de l'utilisateur ou du processus qui a démarré le serveur de développement [!INCLUDE[vstecasp](../misc/includes/vstecasp_md.md)]. Ceci réduit les menaces pour la sécurité. Toutefois, WCF exécute également sa propre authentification et n'autorise pas un compte non\-administrateur à consommer des services WCF.  
  
 Si un utilisateur distant est susceptible d'exécuter le site Web à l'aide du serveur de développement [!INCLUDE[vstecasp](../misc/includes/vstecasp_md.md)] et d'utiliser également un service Web ou WCF, vous pouvez créer une liaison de service personnalisée ou désactiver la sécurité NTLM.  
  
> [!IMPORTANT]
>  Il n'est pas recommandé de désactiver la sécurité NTLM car cela pourrait constituer une menace pour la sécurité.  
  
 Si vous créez une liaison de service personnalisée, vous êtes encore protégé par l'authentification NTLM.  
  
 Effectuez les étapes suivantes pour créer une liaison de service personnalisée pour le service WCF.  
  
#### Pour créer une liaison de service personnalisée pour le service WCF hébergé dans le serveur de développement ASP.NET.  
  
1.  Ouvrez le fichier Web.config pour le service WCF qui génère l'exception.  
  
2.  Entrez les informations suivantes dans le fichier Web.config.  
  
    ```  
    <bindings> <customBinding> <binding name="Service1Binding"> <transactionFlow /> <textMessageEncoding /> <httpTransport authenticationScheme="Ntlm" /> </binding> </customBinding> </bindings>  
    ```  
  
3.  Enregistrez et fermez le fichier Web.config.  
  
4.  Dans le code du service Web ou WCF, modifiez la valeur du point de terminaison comme suit :  
  
    ```  
    <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
    ```  
  
     Ceci garantit que le service utilise la liaison personnalisée.  
  
5.  Ajoutez une référence au service dans l'application Web qui accède au service. \(Dans la boîte de dialogue **Ajouter une référence de service**, ajoutez une référence au service comme vous l'avez fait avec le service original qui générait l'exception.\).  
  
 Vous pouvez suivre les étapes ci\-dessous pour désactiver la sécurité NTLM lorsque vous utilisez une référence de service WCF.  
  
> [!IMPORTANT]
>  Il n'est pas recommandé de désactiver la sécurité NTLM car cela pourrait constituer une menace pour la sécurité.  
  
#### Pour désactiver la sécurité NTLM  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du site Web, puis cliquez sur **Pages de propriétés**.  
  
2.  Sélectionnez **Options de démarrage**, puis désactivez la case à cocher **Authentification NTLM**.  
  
3.  Cliquez sur **OK**.  
  
## Voir aussi  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)