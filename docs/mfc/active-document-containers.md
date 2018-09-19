---
title: Conteneurs de documents actifs | Microsoft Docs
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
ms.openlocfilehash: de03bc7b08a0fe5ae3b1c34fd1a7ec79c8fb0661
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017571"
---
# <a name="active-document-containers"></a>Conteneurs de documents actifs
Un conteneur de documents actifs, tels que le classeur Microsoft Office ou Internet Explorer, vous permet de travailler avec plusieurs documents de différents types d’applications au sein d’un frame unique (au lieu de vous obliger à créer et utiliser plusieurs frames d’application pour chaque type de document).  
  
 MFC fournit la prise en charge complète pour les conteneurs de documents actifs dans le `COleDocObjectItem` classe. Vous pouvez utiliser l’Assistant Application MFC pour créer un conteneur de documents actifs en sélectionnant le **conteneur de documents actifs** case à cocher sur la **prise en charge des documents composés** page de l’Assistant Application MFC. Pour plus d’informations, consultez [création d’une Application de conteneur de Document Active](../mfc/creating-an-active-document-container-application.md).  
  
 Pour plus d’informations sur les conteneurs de documents actifs, consultez :  
  
-   [Conditions requises du conteneur](#container_requirements)  
  
-   [Objets de Site de document](#document_site_objects)  
  
-   [Afficher les objets de Site](#view_site_objects)  
  
-   [Cadrer sur l’objet](#frame_object)  
  
-   [Fusion des menus Aide](../mfc/help-menu-merging.md)  
  
-   [Impression par programmation](../mfc/programmatic-printing.md)  
  
-   [Cibles de la commande](../mfc/message-handling-and-command-targets.md)  
  
##  <a name="container_requirements"></a> Conditions requises du conteneur  
 Prise en charge de document actif dans un conteneur de documents actifs implique plus que des implémentations d’interface : cela nécessite également des connaissances de l’aide des interfaces d’un objet de relation contenant-contenu. Il en va de même pour les extensions de document actif, où le conteneur doit également savoir comment utiliser ces interfaces d’extension sur les documents actifs eux-mêmes.  
  
 Un conteneur de documents actifs qui intègre des documents actifs doit :  
  
-   Être capable de gérer le stockage d’objets via le `IPersistStorage` interface, autrement dit, elle doit fournir un `IStorage` instance à chaque document actif.  
  
-   Prend en charge les fonctionnalités d’incorporation de base des documents OLE, nécessitant des objets « site » (un par document ou incorporation) qui implémentent `IOleClientSite` et `IAdviseSink`.  
  
-   Prend en charge l’activation sur place des objets incorporés ou des documents actifs. Objets de site du conteneur doivent implémenter `IOleInPlaceSite` et objet frame du conteneur doit fournir `IOleInPlaceFrame`.  
  
-   Prend en charge les extensions des documents actifs en implémentant `IOleDocumentSite` pour fournir le mécanisme pour le conteneur communiquer avec le document. Si vous le souhaitez, le conteneur peut implémenter les interfaces de document actif `IOleCommandTarget` et `IContinueCallback` à assimiler les commandes simples telles que l’impression ou l’enregistrement.  
  
 L’objet de frame, les objets de vue et l’objet conteneur peuvent éventuellement implémenter `IOleCommandTarget` pour prendre en charge la distribution de certaines commandes, comme indiqué dans [cibles de la commande](../mfc/message-handling-and-command-targets.md). Affichage et le conteneur objets peuvent également implémenter `IPrint` et `IContinueCallback`, pour prendre en charge l’impression par programmation, comme indiqué dans [impression par programmation](../mfc/programmatic-printing.md).  
  
 La figure suivante montre les relations conceptuelles entre un conteneur et ses composants (à gauche) et le document actif et ses vues (à droite). Le document actif gère le stockage et les données, et la vue affiche ou imprime ces données. Les interfaces en gras sont celles requises pour la participation du document actif ; ces caractères gras et italiques sont facultatifs. Toutes les autres interfaces sont nécessaires.  
  
 ![Interfaces de conteneur de document actif](../mfc/media/vc37gj1.gif "vc37gj1")  
  
 Un document qui prend en charge qu’une seule vue peut implémenter des composants de la vue et le document (autrement dit, leurs interfaces correspondantes) sur une seule classe concrète. En outre, un site conteneur qui prend uniquement en charge une seule vue à la fois peut combiner le site de document et le site de vue dans une classe unique site concrète. Objet de frame du conteneur, cependant, doive rester deux choses distincte et composant de document du conteneur est simplement inclus ici pour donner une image complète de l’architecture ; Il n’est pas affectée par l’architecture de relation contenant-contenu de document actif.  
  
##  <a name="document_site_objects"></a> Objets de Site de document  
 Dans l’architecture de relation contenant-contenu de document actif, un site de document est identique à un objet de site client dans les Documents OLE avec l’ajout de la `IOleDocument` interface :  

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```  
  
 Le site de documents est conceptuellement le conteneur pour un ou plusieurs objets « afficher le site ». Chaque objet de site de vue est associé aux objets de vue individuelle du document géré par le site de document. Si le conteneur prend uniquement en charge une seule vue par site de document, elle peut implémenter le site de document et le site de vue avec une seule classe concrète.  
  
##  <a name="view_site_objects"></a> Afficher les objets de Site  
 Objet de site de vue d’un conteneur gère l’espace d’affichage pour une vue particulière d’un document. La prise en charge la norme `IOleInPlaceSite` interface, un site de vue implémente également généralement `IContinueCallback` pour contrôle d’impression par programmation. (Notez que l’objet de vue interroge jamais pour `IContinueCallback` afin qu’il peut être implémenté sur tout objet le souhait de conteneur.)  
  
 Un conteneur qui prend en charge plusieurs vues doit être en mesure de créer plusieurs vue des objets de site au sein du site de document. Ainsi, chaque vue avec les services d’activation et désactivation distincts comme ceux fournis via `IOleInPlaceSite`.  
  
##  <a name="frame_object"></a> Objet frame  
 Objet frame du conteneur est la plupart du temps, la même image qui est utilisée pour l’activation sur place dans les Documents OLE, c'est-à-dire, celui qui gère la négociation de menu et barre d’outils. Un objet de vue a accès à cet objet frame via `IOleInPlaceSite::GetWindowContext`, ce qui permet également d’accéder à l’objet conteneur qui représente le document conteneur (qui peut gérer la négociation de la barre d’outils au niveau du volet et énumération d’objets de relation contenant-contenu).  
  
 Un conteneur de documents actifs peut augmenter le frame en ajoutant `IOleCommandTarget`. Cela lui permet de recevoir des commandes lancées dans l’interface utilisateur du document actif de la même façon que cette interface peut permettre à un conteneur d’envoyer les mêmes commandes (telles que **le nouveau fichier**, **Open**,  **Enregistrer en tant que**, **impression**; **Modifier une copie**, **coller**, **Annuler**, etc.) dans un document actif. Pour plus d’informations, consultez [cibles de la commande](../mfc/message-handling-and-command-targets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Documents actifs (contenance)](../mfc/active-document-containment.md)

