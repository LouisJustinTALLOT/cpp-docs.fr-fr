---
title: 'Conteneurs : Fonctionnalités avancées | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2999e82bd05d75cb8637ba7404c36cdc2be047a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932170"
---
# <a name="containers-advanced-features"></a>Conteneurs : fonctionnalités avancées
Cet article décrit les étapes nécessaires pour intégrer des fonctionnalités avancées optionnelles dans des applications de conteneur existantes. Ces fonctionnalités sont :  
  
-   [Une application qui est un conteneur et un serveur](#_core_creating_a_container_server_application)  
  
-   [Un lien OLE vers un objet incorporé](#_core_links_to_embedded_objects)  
  
##  <a name="_core_creating_a_container_server_application"></a> Création d’une Application conteneur/serveur  
 Une application conteneur/serveur est une application qui joue à la fois le rôle de conteneur et de serveur. Microsoft Word pour Windows en est un exemple. Vous pouvez inclure Word dans d'autres applications, vous pouvez également inclure des éléments dans Word pour les documents Windows. Le processus pour modifier votre application conteneur pour qu'elle soit à la fois un conteneur et un serveur complet (vous ne pouvez pas créer d'application combinaison conteneur/mini-serveur) est semblable au processus de création d'un serveur complet.  
  
 L’article [serveurs : implémentation d’un serveur](../mfc/servers-implementing-a-server.md) répertorie un certain nombre de tâches requises pour implémenter une application serveur. Si vous convertissez une application conteneur en une application conteneur/serveur, vous devrez effectuer certaines de ces mêmes tâches, en ajoutant du code au conteneur. Ce qui suit répertorie les éléments importants à prendre en compte :  
  
-   Le code de conteneur créé par l'Assistant Application initialise déjà le sous-système OLE. Vous n'aurez pas besoin de modifier ni d'ajouter quoi que ce soit pour ce support.  
  
-   Si l'emplacement de la classe de base d'une classe de document est `COleDocument`, remplacez la classe de base par `COleServerDoc`.  
  
-   Remplacez `COleClientItem::CanActivate` pour éviter de modifier des éléments en place lorsque le serveur lui-même permet de modifier sur place.  
  
     Par exemple, l’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md) a incorporé un élément créé par votre application conteneur/serveur. Ouvrez l'application OCLIENT et modifiez sur place l'élément créé par votre application conteneur/serveur. Lorsque vous modifiez les éléments de votre application, vous décidez d’incorporer un élément créé par l’exemple OLE MFC [HIERSVR](../visual-cpp-samples.md). Pour cela, vous ne pouvez pas utiliser l'activation en place. Vous devez entièrement ouvrir HIERSVR pour activer cet élément. Comme la bibliothèque MFC ne prend pas en charge cette fonctionnalité OLE, remplacer `COleClientItem::CanActivate` vous permet de contrôler cette situation et d'empêcher une erreur d'exécution possible dans votre application.  
  
 Si vous créez une application et souhaitez qu'elle s'exécute en tant qu'application conteneur/serveur, choisissez l'option dans la boîte de dialogue Options OLE dans l'Assistant Application et la prise en charge est créée automatiquement. Pour plus d’informations, consultez l’article [vue d’ensemble : création d’un conteneur de contrôle ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Pour plus d'informations sur les exemples de MFC, consultez les exemples MFC.  
  
 Notez que vous ne pouvez pas insérer une application MDI en elle-même. Une application qui est conteneur/serveur ne peut pas être insérée dans elle-même à moins d'être une application SDI.  
  
##  <a name="_core_links_to_embedded_objects"></a> Liens vers des objets incorporés  
 Les liens vers la fonctionnalité d’objets incorporés permet à un utilisateur de créer un document avec un lien OLE vers un objet incorporé dans votre application conteneur. Par exemple, créez un document dans un traitement de texte contenant une feuille de calcul incorporée. Si votre application prend en charge les liens vers des objets incorporés, elle pourrait également coller un lien vers la feuille de calcul contenue dans le document de traitement de texte. Cette fonctionnalité permet à votre application d’utiliser les informations contenues dans la feuille de calcul sans savoir où le traitement de texte l’a initialement obtenue.  
  
#### <a name="to-link-to-embedded-objects-in-your-application"></a>Pour effectuer une liaison vers des objets incorporés dans votre application  
  
1.  Dérivez votre classe de document à partir de `COleLinkingDoc` au lieu de `COleDocument`.  
  
2.  Créer un ID de classe (**CLSID**) pour votre application en utilisant le Générateur d’ID de classe inclus avec les outils de développement OLE.  
  
3.  Enregistrez l'application avec OLE.  
  
4.  Créez un objet `COleTemplateServer` en tant que membre de la classe d'application.  
  
5.  Dans la fonction membre `InitInstance` de la classe d'application, procédez comme suit :  
  
    -   Connectez votre objet `COleTemplateServer` à vos modèles de document en appelant la fonction membre `ConnectTemplate` de l'objet.  
  
    -   Appelez le `COleTemplateServer::RegisterAll` fonction membre pour inscrire tous les objets de classe avec le système OLE.  
  
    -   Appelez `COleTemplateServer::UpdateRegistry`. Le seul paramètre `UpdateRegistry` doit être *OAT_CONTAINER* si l’application n’est pas lancée avec le commutateur « /Embedded ». Cela enregistre l'application en tant que conteneur capable de prendre en charge les liens vers des objets incorporés.  
  
         Si l'application est ouverte avec le commutateur "/Embedded", elle ne doit pas afficher la fenêtre principale, comme une application serveur.  
  
 L’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md) implémente cette fonctionnalité. Pour obtenir un exemple de cette procédure, consultez le `InitInstance` de fonction dans le *OCLIENT. CPP* fichier de cet exemple d’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs](../mfc/containers.md)   
 [Serveurs](../mfc/servers.md)

