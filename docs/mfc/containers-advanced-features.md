---
title: 'Conteneurs : fonctionnalités avancées'
ms.date: 11/04/2016
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
ms.openlocfilehash: a68cc85062f9ca711c453ef98f69a7c5ea114d94
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214355"
---
# <a name="containers-advanced-features"></a>Conteneurs : fonctionnalités avancées

Cet article décrit les étapes nécessaires pour intégrer des fonctionnalités avancées optionnelles dans des applications de conteneur existantes. Ces fonctionnalités sont :

- [Une application qui est à la fois un conteneur et un serveur](#_core_creating_a_container_server_application)

- [Lien OLE vers un objet incorporé](#_core_links_to_embedded_objects)

##  <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Création d’une application conteneur/serveur

Une application conteneur/serveur est une application qui joue à la fois le rôle de conteneur et de serveur. Microsoft Word pour Windows en est un exemple. Vous pouvez inclure Word dans d'autres applications, vous pouvez également inclure des éléments dans Word pour les documents Windows. Le processus pour modifier votre application conteneur pour qu'elle soit à la fois un conteneur et un serveur complet (vous ne pouvez pas créer d'application combinaison conteneur/mini-serveur) est semblable au processus de création d'un serveur complet.

L’article [serveurs : implémentation d’un serveur](../mfc/servers-implementing-a-server.md) répertorie plusieurs tâches requises pour implémenter une application serveur. Si vous convertissez une application conteneur en une application conteneur/serveur, vous devrez effectuer certaines de ces mêmes tâches, en ajoutant du code au conteneur. Ce qui suit répertorie les éléments importants à prendre en compte :

- Le code de conteneur créé par l'Assistant Application initialise déjà le sous-système OLE. Vous n'aurez pas besoin de modifier ni d'ajouter quoi que ce soit pour ce support.

- Si l'emplacement de la classe de base d'une classe de document est `COleDocument`, remplacez la classe de base par `COleServerDoc`.

- Remplacez `COleClientItem::CanActivate` pour éviter de modifier des éléments en place lorsque le serveur lui-même permet de modifier sur place.

   Par exemple, l’exemple MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a incorporé un élément créé par votre application conteneur/serveur. Ouvrez l'application OCLIENT et modifiez sur place l'élément créé par votre application conteneur/serveur. Lors de la modification de l’élément de votre application, vous décidez d’incorporer un élément créé par l’exemple MFC OLE [HIERSVR](../overview/visual-cpp-samples.md). Pour cela, vous ne pouvez pas utiliser l'activation en place. Vous devez entièrement ouvrir HIERSVR pour activer cet élément. Comme la bibliothèque MFC ne prend pas en charge cette fonctionnalité OLE, remplacer `COleClientItem::CanActivate` vous permet de contrôler cette situation et d’empêcher une erreur d’exécution possible dans votre application.

Si vous créez une application et souhaitez qu'elle s'exécute en tant qu'application conteneur/serveur, choisissez l'option dans la boîte de dialogue Options OLE dans l'Assistant Application et la prise en charge est créée automatiquement. Pour plus d’informations, consultez l’article [vue d’ensemble : création d’un conteneur de contrôles ActiveX](../mfc/reference/creating-an-mfc-activex-control-container.md). Pour plus d’informations sur les exemples MFC, consultez [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

Notez que vous ne pouvez pas insérer une application MDI en elle-même. Une application qui est conteneur/serveur ne peut pas être insérée dans elle-même à moins d'être une application SDI.

##  <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Liens vers des objets incorporés

Les liens vers la fonction d'objets incorporés permet à un utilisateur de créer un document avec un lien OLE vers un objet incorporé dans votre application conteneur. Par exemple, créez un document dans un traitement de texte contenant une feuille de calcul incorporée. Si votre application prend en charge les liens vers des objets incorporés, elle pourrait également coller un lien vers la feuille de calcul contenue dans le document de traitement de texte. Cette fonctionnalité permet à votre application d'utiliser les informations contenues dans la feuille de calcul sans savoir où le traitement de texte l'a initialement obtenue.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>Pour effectuer une liaison vers des objets incorporés dans votre application

1. Dérivez votre classe de document à partir de `COleLinkingDoc` au lieu de `COleDocument`.

1. Créez un ID de classe (**CLSID**) OLE pour votre application en utilisant le générateur d’ID de classe inclus avec les outils de développement OLE.

1. Enregistrez l'application avec OLE.

1. Créez un objet `COleTemplateServer` en tant que membre de la classe d'application.

1. Dans la fonction membre `InitInstance` de la classe d'application, procédez comme suit :

   - Connectez votre objet `COleTemplateServer` à vos modèles de document en appelant la fonction membre `ConnectTemplate` de l'objet.

   - Appelez la fonction membre `COleTemplateServer::RegisterAll` pour inscrire tous les objets de classe auprès du système OLE.

   - Appelez `COleTemplateServer::UpdateRegistry`. Le seul paramètre à `UpdateRegistry` doit être *OAT_CONTAINER* si l’application n’est pas lancée avec le commutateur « /Embedded ». Cela enregistre l'application en tant que conteneur capable de prendre en charge les liens vers des objets incorporés.

      Si l'application est ouverte avec le commutateur "/Embedded", elle ne doit pas afficher la fenêtre principale, comme une application serveur.

L’exemple MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) implémente cette fonctionnalité. Pour obtenir un exemple de cette opération, consultez la fonction `InitInstance` dans *OCLIENT. Fichier CPP* de cet exemple d’application.

## <a name="see-also"></a>Voir aussi

[Containers](../mfc/containers.md)<br/>
[Serveurs](../mfc/servers.md)
