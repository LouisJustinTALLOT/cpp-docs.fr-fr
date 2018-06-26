---
title: Documents actifs sur Internet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], creating
- application wizards [MFC], active documents
- active documents [MFC], programming steps
- application wizards [MFC]
- active documents [MFC], using application wizards
ms.assetid: a46bd8a0-e27a-4116-b1bf-dacdb7ae78d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a18b84b30445060631589e72f6c158ea9b3626f0
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930886"
---
# <a name="active-documents-on-the-internet"></a>Documents actifs sur Internet
Les documents actifs fournissent une extension aux objets incorporés classiques. Les documents actifs peuvent être multipages et sont affichés dans la zone cliente. Ils exécuter la négociation de menu traditionnels et peuvent être modifiées sur place ainsi que dans une fenêtre ouverte dans l’application serveur. Au lieu d’afficher en tant qu’un petit rectangle entouré d’une bordure hachurée, les documents actifs sont plein cadre et actif toujours en place.  
  
 Documents actifs peuvent être affichés dans un conteneur comme le classeur Microsoft Office, qui offre un moyen pour créer un document composé de différents types de document comme Excel, Word, et votre type de document personnalisé, chacun d’eux peut être modifié une image complète. Documents actifs peuvent également être affichés dans un navigateur, tels que Microsoft Internet Explorer, qui est un conteneur de documents actifs.  
  
 **Avantages du document actif :**  
  
-   Les documents peuvent être affichés plein cadre, dans la fenêtre cliente dans son intégralité.  
  
-   Documents peuvent être ouverts dans une fenêtre d’application séparée.  
  
     Pour le document s’ouvre, l’application d’assistance doit exister sur le client, ou être téléchargée séparément avant de l’application peut s’exécuter. Une visionneuse peut être écrit pour fournir des fonctionnalités limitées (Word, PowerPoint et Excel disposent de visionneuses pour leurs documents). La version complète de l’application peut fournir la prise en charge à l’édition complète.  
  
-   Les documents sont toujours actifs sur place.  
  
-   Commandes de menu appelées à partir du conteneur peuvent être acheminés vers votre document.  
  
-   Les documents peuvent être affichés dans un navigateur Web. Cela fournit une intégration transparente entre vos documents et d’autres pages Web.  
  
     Un utilisateur peut parcourir une page HTML Web, puis une feuille de calcul Excel, puis à un document que vous avez écrit à l’aide de MFC prend en charge pour les documents actifs. L’utilisateur d’accéder à l’aide de l’interface Web familière, en tant que les commutateurs de navigateur en toute transparence entre les menus et les vues d’une page HTML, Excel et les documents de votre application.  
  
-   Toutes les applications sont affichées dans un cadre commun.  
  
## <a name="requirements-for-active-documents"></a>Exigences pour les documents actifs  
 Les interfaces répertoriées dans le tableau ci-dessous incluent les interfaces déjà requises pour les serveurs incorporés et plusieurs nouvelles interfaces spécifiques aux documents actifs. MFC fournit des implémentations par défaut pour la plupart de ces interfaces dans le [COleServerDoc](../mfc/reference/coleserverdoc-class.md) classe.  
  
|Un document qui...|Implémente ces interfaces|  
|-------------------------|---------------------------------|  
|Utilise des fichiers composés comme mécanisme de stockage.|`IPersistStorage`.|  
|Prend en charge les fonctionnalités d’incorporation de base des documents Active, y compris les créer à partir du fichier.|`IPersistFile`, `IOleObject` et `IDataObject`.|  
|Prend en charge l’activation sur place.|`IOleInPlaceObject` et `IOleInPlaceActiveObject` (à l’aide du conteneur `IOleInPlaceSite` et `IOleInPlaceFrame` interfaces).|  
|Prend en charge les extensions de document actif qui impliquent ces nouvelles interfaces. Certaines interfaces sont facultatifs.|`IOleDocument`, `IOleDocumentView`, `IOleCommandTarget` et `IPrint`.|  
  
 MFC prend en charge pour l’extension de la prise en charge de serveur intégré existante pour les documents actifs.  
  
## <a name="add-active-document-support-to-a-new-application"></a>Ajouter la prise en charge du Document actif à une nouvelle Application  
 Pour créer une nouvelle application avec prise en charge des documents actifs : dans l’Assistant Application MFC, dans le **prend en charge les documents composés** sous « prise en charge du document composé sélectionnez » choisissez **serveur complet** ou  **Conteneur/serveur complet**, sous « Sélectionnez des options supplémentaires », activez la case à cocher **serveur de documents actifs**.  
  
##  <a name="_core_convert_an_existing_mfc_in.2d.process_server_to_an_activex_document_server"></a> Convertir un serveur In-Process MFC existant à un serveur de documents actifs  
 Si votre application a été créée avec une version de Visual C++ antérieures à la version 4.2 et est déjà un serveur in-process, vous pouvez ajouter la prise en charge du document actif en apportant des modifications dans les classes suivantes :  
  
|Type de classe|Anciennement dérivé de|Modifier pour dériver de|  
|----------------|---------------------------|---------------------------|  
|Frame en Place|`COleIPFrameWnd`|`COleDocIPFrameWnd`|  
|Élément|`COleServerItem`|`CDocObjectServerItem`|  
  
 Vous également modifier la façon dont les informations sont entrées dans le Registre et effectuer plusieurs autres modifications. Si votre application n’a actuellement aucune prise en charge des composants COM, vous pouvez ajouter la prise en charge du serveur en exécutant l’Assistant Application et en intégrant le code spécifique au composant COM avec votre application existante.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)

