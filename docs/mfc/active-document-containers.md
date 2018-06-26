---
title: Conteneurs de documents actifs | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c912b6c703ef7e05825e070d09f0a1b3cd73003
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932157"
---
# <a name="active-document-containers"></a>Conteneurs de documents actifs
Un conteneur de documents actifs, tels que le classeur Microsoft Office ou Internet Explorer, vous permet de travailler avec plusieurs documents de différents types d’applications au sein d’un frame unique (au lieu de vous obliger à créer et utiliser plusieurs frames d’application pour chaque type de document).  
  
 MFC fournit la prise en charge complète pour les conteneurs de documents actifs dans la `COleDocObjectItem` classe. Vous pouvez utiliser l’Assistant Application MFC pour créer un conteneur de documents actifs en sélectionnant le **conteneur de documents actifs** case à cocher sur la **prise en charge des documents composés** page de l’Assistant Application MFC. Pour plus d’informations, consultez [création d’une Application conteneur de documents actifs](../mfc/creating-an-active-document-container-application.md).  
  
 Pour plus d’informations sur les conteneurs de documents actifs, consultez :  
  
-   [Configuration requise du conteneur](#container_requirements)  
  
-   [Objets document Site](#document_site_objects)  
  
-   [Objets de vue de Site](#view_site_objects)  
  
-   [Cadrer sur l’objet](#frame_object)  
  
-   [Fusion des menus Aide](../mfc/help-menu-merging.md)  
  
-   [Impression par programmation](../mfc/programmatic-printing.md)  
  
-   [Cibles de la commande](../mfc/message-handling-and-command-targets.md)  
  
##  <a name="container_requirements"></a> Configuration requise du conteneur  
 Prise en charge du document actif dans un conteneur de documents actifs implique plusieurs implémentations d’interfaces : elle nécessite également la connaissance de l’aide des interfaces d’un objet contenu. Il en va de même pour les extensions de document actif, où le conteneur doit également savoir utiliser ces interfaces d’extension sur les documents actifs eux-mêmes.  
  
 Un conteneur de documents actifs qui intègre des documents actifs doit :  
  
-   Être capable de gérer le stockage d’objets via la `IPersistStorage` interface, autrement dit, elle doit fournir une `IStorage` instance à chaque document actif.  
  
-   Prend en charge les fonctionnalités d’incorporation de base des documents OLE, nécessitant des objets de « site » (un par document ou incorporation) qui implémentent `IOleClientSite` et `IAdviseSink`.  
  
-   Prend en charge l’activation sur place des objets incorporés ou des documents actifs. Objets de site du conteneur doivent implémenter `IOleInPlaceSite` et objet de frame du conteneur doit fournir `IOleInPlaceFrame`.  
  
-   Prend en charge les extensions du document actif en implémentant `IOleDocumentSite` pour fournir le mécanisme pour le conteneur communiquer avec le document. Si vous le souhaitez, le conteneur peut implémenter les interfaces de document actif `IOleCommandTarget` et `IContinueCallback` pour choisir des commandes simples, comme l’impression ou de l’enregistrement.  
  
 L’objet frame, les objets de vue et l’objet de conteneur peuvent implémenter `IOleCommandTarget` pour prendre en charge la distribution de certaines commandes, comme indiqué dans [cibles de la commande](../mfc/message-handling-and-command-targets.md). Objets View et container peuvent également implémenter `IPrint` et `IContinueCallback`pour prendre en charge l’impression par programmation, comme indiqué dans [impression par programmation](../mfc/programmatic-printing.md).  
  
 L’illustration suivante montre les relations conceptuelles entre un conteneur et ses composants (à gauche) et le document actif et ses vues (à droite). Le document actif gère le stockage et les données et la vue affiche ou imprime ces données. Les interfaces en gras sont celles requises pour la participation de document actif ; Ces valeur en gras et italique sont facultatifs. Toutes les autres interfaces sont requises.  
  
 ![Interfaces de conteneur de documents actifs](../mfc/media/vc37gj1.gif "vc37gj1")  
  
 Un document qui prend en charge qu’une seule vue peut implémenter les composants de la vue et le document (autrement dit, leurs interfaces correspondantes) sur une seule classe concrète. En outre, un site conteneur qui prend uniquement en charge une seule vue à la fois peut combiner les sites document et la vue dans une classe de site concrète unique. Objet de frame du conteneur, cependant, doit rester distincte et composant de document du conteneur est simplement inclus ici pour donner un aperçu complet de l’architecture ; Il n’est pas affecté par l’architecture de relation contenant-contenu de document actif.  
  
##  <a name="document_site_objects"></a> Objets document Site  
 Dans l’architecture de relation contenant-contenu de document actif, un site de document est identique à un objet de site client dans les Documents OLE avec l’ajout de la `IOleDocument` interface :  
  
 `interface IOleDocumentSite : IUnknown`  
  
 `{`  
  
 `HRESULT ActivateMe(IOleDocumentView *pViewToActivate);`  
  
 `}`  
  
 Le site de document est théoriquement le conteneur pour un ou plusieurs objets « afficher le site ». Chaque objet view site est associé à des objets view individuels du document géré par le site de document. Si le conteneur prend uniquement en charge une seule vue par site de document, elle peut implémenter le site de document et le site de vue avec une seule classe concrète.  
  
##  <a name="view_site_objects"></a> Objets de vue de Site  
 Objet de site de vue d’un conteneur gère l’espace d’affichage pour une vue particulière d’un document. Prise en charge de la norme `IOleInPlaceSite` interface, un site de vue implémente également généralement `IContinueCallback` pour le contrôle d’impression par programmation. (Notez que l’objet de vue interroge jamais pour `IContinueCallback` afin qu’il peut être implémenté sur tout objet les conteneur de souhaits.)  
  
 Un conteneur qui prend en charge plusieurs vues doit être en mesure de créer d’affichage de plusieurs objets du site dans le site de document. Cela fournit à chaque vue avec les services d’activation et désactivation distincts tel que fourni par le biais `IOleInPlaceSite`.  
  
##  <a name="frame_object"></a> Objet frame  
 Objet de frame du conteneur est, par la plupart des cas, la même image que celle qui est utilisée pour l’activation sur place dans les Documents OLE, c'est-à-dire, celui qui gère la négociation de menu et barre d’outils. Un objet de vue a accès à cet objet frame via `IOleInPlaceSite::GetWindowContext`, ce qui permet également d’accéder à l’objet conteneur qui représente le document conteneur (qui peut gérer la négociation de la barre d’outils du volet niveau et l’énumération d’objets contenus).  
  
 Un conteneur de documents actifs peut augmenter le frame en ajoutant `IOleCommandTarget`. Cela lui permet de recevoir des commandes lancées dans l’interface utilisateur du document actif de la même manière que cette interface peut permettre à un conteneur d’envoyer les mêmes commandes (telles que **le nouveau fichier**, **ouvrir**,  **Enregistrer en tant que**, **impression**; **Modifier une copie**, **coller**, **Annuler**, etc.) dans un document actif. Pour plus d’informations, consultez [cibles de la commande](../mfc/message-handling-and-command-targets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Documents actifs (contenance)](../mfc/active-document-containment.md)

