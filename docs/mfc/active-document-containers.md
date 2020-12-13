---
description: 'En savoir plus sur : conteneurs de documents actifs'
title: Conteneurs de documents actifs
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: 31cf2739595cb7a48b152dcefb6c21970b95f8bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150408"
---
# <a name="active-document-containers"></a>Conteneurs de documents actifs

Un conteneur de documents actifs, tel que Microsoft Office Binder ou Internet Explorer, vous permet de travailler avec plusieurs documents de différents types d’application au sein d’un seul Frame (au lieu de vous forcer à créer et à utiliser plusieurs frames d’application pour chaque type de document).

MFC offre une prise en charge complète des conteneurs de documents actifs dans la `COleDocObjectItem` classe. Vous pouvez utiliser l’Assistant Application MFC pour créer un conteneur de documents actifs en activant la case à cocher **conteneur de documents actifs** sur la page **prise en charge des documents composés** de l’Assistant Application MFC. Pour plus d’informations, consultez [création d’une application de conteneur de documents actifs](creating-an-active-document-container-application.md).

Pour plus d’informations sur les conteneurs de documents actifs, consultez :

- [Conditions requises pour le conteneur](#container_requirements)

- [Objets de site de document](#document_site_objects)

- [Afficher les objets de site](#view_site_objects)

- [Cadrer sur l’objet](#frame_object)

- [Fusion du menu aide](help-menu-merging.md)

- [Impression par programmation](programmatic-printing.md)

- [Cibles de commande](message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a> Conditions requises pour le conteneur

La prise en charge des documents actifs dans un conteneur de documents actifs implique plus que des implémentations d’interface simples : elle nécessite également d’utiliser les interfaces d’un objet contenu. Il en va de même pour les extensions de documents actifs, où le conteneur doit également savoir comment utiliser ces interfaces d’extension sur les documents actifs eux-mêmes.

Un conteneur de documents actifs qui intègre des documents actifs doit :

- Être capable de gérer le stockage d’objets par le biais de l' `IPersistStorage` interface, autrement dit, il doit fournir une `IStorage` instance à chaque document actif.

- Prendre en charge les fonctionnalités d’incorporation de base des documents OLE, nécessitant des objets « site » (un par document ou une incorporation) qui implémentent `IOleClientSite` et `IAdviseSink` .

- La prise en charge de l’activation sur place des objets incorporés ou des documents actifs. Les objets de site du conteneur doivent implémenter `IOleInPlaceSite` et l’objet de frame du conteneur doit fournir `IOleInPlaceFrame` .

- Prendre en charge les extensions des documents actifs en implémentant `IOleDocumentSite` pour fournir le mécanisme permettant au conteneur de communiquer avec le document. Si vous le souhaitez, le conteneur peut implémenter les interfaces de document actives `IOleCommandTarget` et `IContinueCallback` Sélectionner des commandes simples telles que l’impression ou l’enregistrement.

L’objet Frame, les objets de vue et l’objet conteneur peuvent éventuellement implémenter `IOleCommandTarget` pour prendre en charge la distribution de certaines commandes, comme indiqué dans [commandes targets](message-handling-and-command-targets.md). Les objets de vue et de conteneur peuvent également éventuellement implémenter `IPrint` et `IContinueCallback` , pour prendre en charge l’impression par programme, comme indiqué dans [impression par programmation](programmatic-printing.md).

L’illustration suivante montre les relations conceptuelles entre un conteneur et ses composants (à gauche), ainsi que le document actif et ses vues (à droite). Le document actif gère le stockage et les données, et la vue affiche ou imprime éventuellement ces données. Les interfaces en gras sont celles requises pour la participation aux documents actifs. les caractères gras et italique sont facultatifs. Toutes les autres interfaces sont requises.

![Interfaces actives de conteneurs de documents](../mfc/media/vc37gj1.gif "Interfaces actives de conteneurs de documents")

Un document qui ne prend en charge qu’une seule vue peut implémenter à la fois les composants vue et document (autrement dit, leurs interfaces correspondantes) sur une seule classe concrète. En outre, un site conteneur qui ne prend en charge qu’une seule vue à la fois peut combiner le site de documents et le site d’affichage dans une seule classe de site concrète. Toutefois, l’objet frame du conteneur doit rester distinct et le composant document du conteneur est simplement inclus ici pour obtenir une image complète de l’architecture. elle n’est pas affectée par l’architecture de relation contenant-contenu de document actif.

## <a name="document-site-objects"></a><a name="document_site_objects"></a> Objets de site de document

Dans l’architecture de relation contenant-contenu de document actif, un site de document est le même qu’un objet de site client dans les documents OLE, avec l’ajout de l' `IOleDocument` interface :

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

Le site de document est conceptuellement le conteneur pour un ou plusieurs objets « afficher le site ». Chaque objet de site d’affichage est associé à des objets de vue individuels du document géré par le site de document. Si le conteneur ne prend en charge qu’une seule vue par site de document, il peut implémenter le site de document et le site d’affichage avec une seule classe concrète.

## <a name="view-site-objects"></a><a name="view_site_objects"></a> Afficher les objets de site

L’objet de site View d’un conteneur gère l’espace d’affichage d’une vue particulière d’un document. Outre la prise en charge de l' `IOleInPlaceSite` interface standard, un site d’affichage implémente également le `IContinueCallback` contrôle d’impression par programmation. (Notez que l’objet de vue ne fait jamais l’objet de requêtes pour `IContinueCallback` qu’il puisse être implémenté sur n’importe quel objet que le conteneur désire.)

Un conteneur qui prend en charge plusieurs vues doit pouvoir créer plusieurs objets de site de vue dans le site de document. Cela fournit chaque vue avec des services d’activation et de désactivation distincts, fournis par le biais de `IOleInPlaceSite` .

## <a name="frame-object"></a><a name="frame_object"></a> Objet Frame

L’objet frame du conteneur est, pour l’essentiel, le même frame que celui utilisé pour l’activation sur place dans les documents OLE, autrement dit, celui qui gère la négociation des menus et des barres d’outils. Un objet de vue a accès à cet objet de frame via `IOleInPlaceSite::GetWindowContext` , qui permet également d’accéder à l’objet conteneur représentant le document conteneur (qui peut gérer la négociation de barre d’outils au niveau du volet et l’énumération d’objets contenus).

Un conteneur de documents actifs peut augmenter le frame en ajoutant `IOleCommandTarget` . Cela lui permet de recevoir des commandes qui proviennent de l’interface utilisateur du document actif, de la même façon que cette interface peut autoriser un conteneur à envoyer les mêmes commandes (telles que **fichier nouveau**, **ouvrir**, **Enregistrer sous**, **Imprimer**; **Modifiez copier**, **coller**, **Annuler** et autres) dans un document actif. Pour plus d’informations, consultez [cibles de commande](message-handling-and-command-targets.md).

## <a name="see-also"></a>Voir aussi

[Relation contenant-contenu de document actif](active-document-containment.md)
