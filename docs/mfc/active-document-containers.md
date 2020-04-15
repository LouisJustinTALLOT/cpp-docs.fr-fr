---
title: Conteneurs de documents actifs
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: e2005ffed592fa1de278e0f6339d94687a20fd06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377382"
---
# <a name="active-document-containers"></a>Conteneurs de documents actifs

Un conteneur de documents actif, tel que Microsoft Office Binder ou Internet Explorer, vous permet de travailler avec plusieurs documents de différents types d’applications dans un seul cadre (au lieu de vous forcer à créer et à utiliser plusieurs cadres d’application pour chaque type de document).

MFC fournit un soutien complet `COleDocObjectItem` pour les conteneurs de documents actifs dans la classe. Vous pouvez utiliser l’assistant d’application MFC pour créer un conteneur de documents actif en sélectionnant la case **à cocher des conteneurs de documents actifs** sur la page de support de document **composé** de l’assistant d’application MFC. Pour plus d’informations, voir [Création d’une application de conteneurs de documents actifs](../mfc/creating-an-active-document-container-application.md).

Pour plus d’informations sur les conteneurs de documents actifs, voir :

- [Exigences relatives aux conteneurs](#container_requirements)

- [Objets de site de document](#document_site_objects)

- [Afficher les objets du site](#view_site_objects)

- [Cadrer sur l’objet](#frame_object)

- [Fusion des menus Aide](../mfc/help-menu-merging.md)

- [Impression programmatique](../mfc/programmatic-printing.md)

- [Cibles de la commande](../mfc/message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>Exigences relatives aux conteneurs

Le support de document actif dans un conteneur de documents actif implique plus qu’une simple implémentation d’interface : il nécessite également la connaissance de l’utilisation des interfaces d’un objet contenu. Il en va de même pour les extensions de documents actives, où le conteneur doit également savoir comment utiliser ces interfaces d’extension sur les documents actifs eux-mêmes.

Un conteneur de documents actif qui intègre les documents actifs doit :

- Soyez capable de manipuler `IPersistStorage` le stockage d’objets à `IStorage` travers l’interface, c’est-à-dire qu’il doit fournir une instance à chaque document actif.

- Prendre en charge les caractéristiques d’intégration de base des documents OLE, nécessitant `IOleClientSite` `IAdviseSink`des objets « site » (un par document ou intégration) qui implémentent et .

- Prendre en charge l’activation sur place d’objets embarqués ou de documents actifs. Les objets du site `IOleInPlaceSite` du conteneur doivent être mis `IOleInPlaceFrame`en œuvre et l’objet cadre du conteneur doit fournir.

- Soutenez les extensions des `IOleDocumentSite` documents actifs en mettant en œuvre le mécanisme permettant au conteneur de parler au document. En option, le conteneur peut implémenter les interfaces de documents actives `IOleCommandTarget` et `IContinueCallback` prendre des commandes simples telles que l’impression ou l’enregistrement.

L’objet cadre, les objets de vue et `IOleCommandTarget` l’objet du conteneur peuvent être mis en œuvre de manière optionnelle pour soutenir l’envoi de certaines commandes, comme le sont les [cibles de commandement](../mfc/message-handling-and-command-targets.md). Les objets de vue et `IPrint` `IContinueCallback`de conteneur peuvent également implémenter en option et, pour soutenir l’impression programmatique, comme discuté dans [l’impression programmatique](../mfc/programmatic-printing.md).

Le chiffre suivant montre les relations conceptuelles entre un conteneur et ses composants (à gauche), et le document actif et ses vues (à droite). Le document actif gère le stockage et les données, et la vue affiche ou imprime optionnellement ces données. Les interfaces en gras sont celles requises pour la participation active aux documents; gras et italiques sont facultatifs. Toutes les autres interfaces sont nécessaires.

![Interfaces actives de conteneurs de documents](../mfc/media/vc37gj1.gif "Interfaces actives de conteneurs de documents")

Un document qui ne prend en charge qu’une seule vue peut implémenter à la fois les composants de vue et de document (c’est-à-dire leurs interfaces correspondantes) sur une seule classe concrète. En outre, un site de conteneurs qui ne prend en charge qu’une vue à la fois peut combiner le site de document et le site de vue en une seule classe de site en béton. L’objet cadre du conteneur, cependant, doit rester distinct, et le composant de document du conteneur est simplement inclus ici pour donner une image complète de l’architecture; elle n’est pas affectée par l’architecture active de confinement des documents.

## <a name="document-site-objects"></a><a name="document_site_objects"></a>Objets de site de document

Dans l’architecture active de confinement des documents, un site document est le même `IOleDocument` qu’un objet de site client dans OLE Documents avec l’ajout de l’interface :

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

Le site de documents est conceptuellement le conteneur d’un ou de plusieurs objets de « site de vue ». Chaque objet de site de vue est associé aux objets de vue individuels du document géré par le site du document. Si le conteneur ne prend en charge qu’une seule vue par site document, il peut implémenter le site du document et le site de vue avec une seule classe en béton.

## <a name="view-site-objects"></a><a name="view_site_objects"></a>Afficher les objets du site

L’objet de vue d’un conteneur gère l’espace d’affichage pour une vue particulière d’un document. En plus de `IOleInPlaceSite` prendre en charge l’interface `IContinueCallback` standard, un site de vue implémente généralement pour le contrôle de l’impression programmatique. (Notez que l’objet `IContinueCallback` de vue ne requête jamais pour qu’il puisse effectivement être mis en œuvre sur n’importe quel objet souhaité par le conteneur.)

Un conteneur qui prend en charge plusieurs vues doit être en mesure de créer plusieurs objets de site de vue dans le site de document. Cela fournit chaque vue avec des services d’activation et de désactivation distincts tels que fournis par le biais `IOleInPlaceSite`.

## <a name="frame-object"></a><a name="frame_object"></a>Objet de cadre

L’objet cadre du conteneur est, pour la plupart, le même cadre qui est utilisé pour l’activation en place dans OLE Documents, c’est-à-dire celui qui gère le menu et la négociation de barres d’outils. Un objet de vue a `IOleInPlaceSite::GetWindowContext`accès à cet objet cadre à travers , qui donne également accès à l’objet conteneur représentant le document de conteneur (qui peut gérer la négociation de barre d’outils au niveau de la vitre et l’énumération des objets contenus).

Un conteneur de documents actif `IOleCommandTarget`peut augmenter le cadre en ajoutant . Cela lui permet de recevoir des commandes qui proviennent de l’interface utilisateur du document actif de la même manière que cette interface peut permettre à un conteneur d’envoyer les mêmes commandes (tels que **File New**, **Open**, **Save As**, **Imprimer**; **Modifier La copie,** **la pâte,** **annuler,** et d’autres) à un document actif. Pour plus d’informations, voir [Cibles de commandement](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Voir aussi

[Documents actifs (contenance)](../mfc/active-document-containment.md)
