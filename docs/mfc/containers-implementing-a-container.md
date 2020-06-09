---
title: "Conteneurs : implémentation d'un conteneur"
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 0ba8d4aea6b69fdbfeedfba59449d0d30433eb94
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623228"
---
# <a name="containers-implementing-a-container"></a>Conteneurs : implémentation d'un conteneur

Cet article résume la procédure permettant d'implémenter un conteneur et vous présente d'autres articles qui fournissent des explications détaillées sur l'implémentation des conteneurs. Il répertorie également des fonctionnalités OLE optionnelles que vous pouvez souhaiter implémenter et les articles décrivant ces fonctionnalités.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>Pour préparer votre classe dérivée de CWinApp

1. Initialisez les bibliothèques OLE en appelant `AfxOleInit` dans la `InitInstance` fonction membre.

1. Appelez `CDocTemplate::SetContainerInfo` dans `InitInstance` pour affecter le menu et les ressources accélératrices utilisés lorsqu'un élément incorporé est activé en place. Pour plus d’informations sur cette rubrique, consultez [activation](activation-cpp.md).

Ces fonctionnalités sont fournies automatiquement lorsque vous utilisez l'Assistant Application MFC pour créer une application conteneur. Consultez [création d’un programme exe MFC](reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>Pour préparer votre classe d'affichage

1. Conservez les éléments sélectionnés en maintenant un pointeur, ou une liste des pointeurs si vous prenez en charge la sélection multiple, vers les éléments sélectionnés. Votre fonction `OnDraw` doit afficher tous les éléments OLE.

1. Remplacez `IsSelected` pour vérifier si l'élément qui lui est passé est sélectionné.

1. Implémentez un `OnInsertObject` Gestionnaire de messages pour afficher la boîte de dialogue **Insérer un objet** .

1. Implémentez un gestionnaire de messages `OnSetFocus` pour transférer le focus depuis la vue sur un élément incorporé OLE actif en place.

1. Implémenter un gestionnaire de messages `OnSize` pour indiquer à un élément incorporé OLE qu'il doit modifier son rectangle pour refléter les modifications de taille de la vue conteneur.

Étant donné que l’implémentation de ces fonctionnalités varie excessivement d’une application à l’autre, l’application ne fournit qu’une implémentation de base. Vous devrez vraisemblablement personnaliser ces fonctions pour que l'application fonctionne correctement. Pour obtenir un exemple, consultez l’exemple [Container](../overview/visual-cpp-samples.md) .

#### <a name="to-handle-embedded-and-linked-items"></a>Pour traiter des éléments incorporés et liés

1. Dérivez une classe de [COleClientItem](reference/coleclientitem-class.md). Les objets de cette classe représentent les éléments qui ont été incorporés ou liés à votre document OLE.

1. Substituez `OnChange` , `OnChangeItemPosition` et `OnGetItemPosition` . Ces fonctions gèrent le dimensionnement, le positionnement et la modification d'éléments liés et incorporés.

L’Assistant Application dérivera la classe pour vous, mais vous devrez probablement remplacer `OnChange` et les autres fonctions listées à l’étape 2 de la procédure précédente. Les implémentations squelette doivent être personnalisées pour la plupart des applications, car ces fonctions sont implémentées de manière différente d'une application à l'autre. Pour obtenir des exemples, consultez le conteneur [DRAWCLI](../overview/visual-cpp-samples.md) et [Container](../overview/visual-cpp-samples.md)des exemples MFC.

Vous devez ajouter plusieurs éléments à la structure du menu de l'application conteneur pour prendre en charge OLE. Pour plus d’informations, consultez [menus et ressources : ajouts de conteneurs](menus-and-resources-container-additions.md).

Vous pouvez aussi prendre en charge certaines des fonctionnalités suivantes dans votre application conteneurs :

- Activation en place lors de la modification d'un élément incorporé.

   Pour plus d’informations, consultez [activation](activation-cpp.md).

- Création d'éléments OLE par glissement-déplacement d'une sélection depuis une application serveur.

   Pour plus d’informations, consultez [glisser-déplacer OLE](drag-and-drop-ole.md).

- Liens vers les objets incorporés ou association des applications conteneur/serveur.

   Pour plus d’informations, consultez [conteneurs : fonctionnalités avancées](containers-advanced-features.md).

## <a name="see-also"></a>Voir aussi

[Containers](containers.md)<br/>
[Conteneurs : éléments clients](containers-client-items.md)
