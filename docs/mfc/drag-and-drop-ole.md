---
title: Glisser-déposer OLE
description: Vue d’ensemble de la fonctionnalité glisser-déplacer OLE Microsoft Foundation Classes (MFC), comment implémenter une source de dépôt, une cible de déplacement et comment personnaliser le glisser-déplacer.
ms.date: 02/09/2020
helpviewer_keywords:
- OLE server applications [MFC], drag and drop
- drag and drop [MFC]
- OLE applications [MFC], drag and drop
- File Manager drag and drop support [MFC]
- drag and drop [MFC], about OLE drag and drop
- OLE drag and drop [MFC]
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
ms.openlocfilehash: 23680765377d325bdc1f8878daf4d4fc553a1304
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623188"
---
# <a name="ole-drag-and-drop"></a>Glisser-déposer OLE

La fonctionnalité glisser-déposer de l’OLE est essentiellement un raccourci pour copier et coller des données. Lorsque vous utilisez le Presse-papiers pour copier et coller des données, un certain nombre d'étapes sont nécessaires. Sélectionnez les données, puis choisissez **couper** ou **copier** dans le menu **Edition** . Ensuite, vous accédez à l’application ou à la fenêtre de destination et placez le curseur à l’emplacement cible. Enfin, vous choisissez **Edition**  >  **coller** dans le menu.

La fonctionnalité glisser-déplacer OLE est différente du mécanisme de glisser-déplacer du gestionnaire de fichiers. Le gestionnaire de fichiers peut uniquement gérer les noms de fichiers et est conçu spécifiquement pour transmettre les noms de fichiers aux applications. Le glisser-déplacer dans OLE est bien plus général. Vous pouvez ainsi faire glisser toutes les données qui peuvent être placées dans le Presse-papiers.

Lorsque vous utilisez la fonction Glisser-déplacer OLE, vous supprimez deux étapes du processus. Vous sélectionnez les données dans la fenêtre source (la « source de dépôt »), puis vous les faites glisser vers la destination (la « cible de déplacement »). Vous la déposez en relâchant le bouton de la souris. L’opération élimine le besoin de menus et est plus rapide que la séquence de copie/collage. Il n’existe qu’une seule exigence : la source de dépôt et la cible de dépôt doivent être ouvertes et au moins partiellement visibles à l’écran.

À l’aide de la fonction glisser-déplacer OLE, les données peuvent être transférées facilement d’un emplacement à un autre : dans un document, entre différents documents ou entre des applications. Elle peut être implémentée dans un conteneur ou une application serveur. Toute application peut être une source de dépôt, une cible de dépôt, ou les deux. Si une application implémente la prise en charge de la source de dépôt et de la cible de dépôt, vous pouvez effectuer un glisser-déplacer entre les fenêtres enfants, ou dans une fenêtre. Cette fonctionnalité rend votre application beaucoup plus facile à utiliser.

Les articles sur les [objets de données et les sources de données (OLE)](data-objects-and-data-sources-ole.md) expliquent comment implémenter le transfert de données dans vos applications. Il est également utile d’examiner les exemples OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="implement-a-drop-source"></a><a name="implement-a-drop-source"></a>Implémenter une source de dépôt

Pour faire en sorte que votre application fournisse des données à une opération de glisser-déplacer, vous devez implémenter une source de déplacement. L’implémentation de base d’une source de déplacement est relativement simple. La première étape consiste à déterminer les événements qui commencent une opération glisser. Les instructions d’interface utilisateur recommandées définissent le début d’une opération glisser comme lorsqu’un événement **WM_LBUTTONDOWN** se produit sur un point à l’intérieur de certaines données sélectionnées. Les exemples OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md) suivent ces instructions.

Si votre application est un conteneur et que les données sélectionnées sont un objet lié ou incorporé de type `COleClientItem` , appelez la `DoDragDrop` fonction membre. Sinon, construisez un `COleDataSource` objet, initialisez-le avec la sélection et appelez la fonction membre de l’objet de source de données `DoDragDrop` . Si votre application est un serveur, utilisez `COleServerItem::DoDragDrop` . Pour plus d’informations sur la personnalisation du comportement de glisser-déplacer standard, consultez la section [personnaliser le glisser-déplacer](#customize-drag-and-drop).

Si `DoDragDrop` retourne **DROPEFFECT_MOVE**, supprimez immédiatement les données sources du document source. Aucune autre valeur de retour de n' `DoDragDrop` a d’effet sur une source de déplacement.

Pour plus d’informations, consultez [objets de données OLE et sources de données : création et destruction](data-objects-and-data-sources-creation-and-destruction.md) , [objets de données OLE et sources de données : manipulation](data-objects-and-data-sources-manipulation.md)\.

## <a name="implement-a-drop-target"></a><a name="implement-a-drop-target"></a>Implémenter une cible de déplacement

Il faut un peu plus de travail pour implémenter une cible de déplacement qu’une source de déplacement, mais cela reste relativement simple.

### <a name="to-implement-an-ole-drop-target"></a>Pour implémenter une cible de déplacement OLE

1. Si ce n’est pas déjà fait, ajoutez un appel à `AfxOleInit` dans la `InitInstance` fonction membre de votre application. Cet appel est requis pour initialiser les bibliothèques OLE.

1. Ajoutez une variable membre à chaque vue de l’application que vous souhaitez utiliser comme cible de dépôt. Cette variable membre doit être de type `COleDropTarget` ou une classe dérivée de celle-ci.

1. À partir de la fonction de votre classe d’affichage qui gère le message d' **WM_CREATE** (en général `OnCreate` ), appelez la fonction membre de la nouvelle variable membre `Register` . `Revoke`est appelé automatiquement lorsque votre vue est détruite.

1. Substituez les fonctions suivantes. Si vous souhaitez obtenir le même comportement dans l’ensemble de votre application, substituez ces fonctions dans votre classe d’affichage. Si vous souhaitez modifier le comportement dans les cas isolés ou si vous souhaitez activer la suppression sur des non- `CView` Windows, substituez ces fonctions dans votre `COleDropTarget` classe dérivée de.

   | Écraser | Pour autoriser |
   | -------- | -------- |
   | `OnDragEnter` | Supprimer les opérations à effectuer dans la fenêtre. Appelé lorsque le curseur entre en première place dans la fenêtre. |
   | `OnDragLeave` | Comportement spécial lorsque l’opération glisser quitte la fenêtre spécifiée. |
   | `OnDragOver` | Supprimer les opérations à effectuer dans la fenêtre. Appelé lorsque le curseur est glissé dans la fenêtre. |
   | `OnDrop` | Gestion des données déplacées dans la fenêtre spécifiée. |
   | `OnScrollBy` | Comportement spécial pour lorsque le défilement est nécessaire dans la fenêtre cible. |

Consultez MAINVIEW. CPP qui fait partie de l’exemple MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) pour obtenir un exemple de la façon dont ces fonctions fonctionnent ensemble.

Pour plus d’informations, consultez [objets de données OLE et sources de données : création et destruction](data-objects-and-data-sources-creation-and-destruction.md) , [objets de données OLE et sources de données : manipulation](data-objects-and-data-sources-manipulation.md)\.

## <a name="customize-drag-and-drop"></a><a name="customize-drag-and-drop"></a>Personnaliser le glisser-déplacer

L’implémentation par défaut de la fonctionnalité de glisser-déplacer est suffisante pour la plupart des applications. Toutefois, certaines applications peuvent vous obliger à modifier ce comportement standard. Cette section explique les étapes nécessaires à la modification de ces paramètres par défaut. Vous pouvez utiliser cette technique pour créer des applications qui ne prennent pas en charge les documents composés dans des sources de dépôt.

Si vous personnalisez le comportement de glisser-déplacer OLE standard ou si vous avez une application non-OLE, vous devez créer un `COleDataSource` objet pour contenir les données. Lorsque l’utilisateur démarre une opération de glisser-déplacer, votre code doit appeler la `DoDragDrop` fonction à partir de cet objet plutôt qu’à partir d’autres classes qui prennent en charge les opérations de glisser-déplacer.

Si vous le souhaitez, vous pouvez créer un `COleDropSource` objet pour contrôler la suppression et remplacer certaines de ses fonctions selon le type de comportement que vous souhaitez modifier. Cet objet source Drop est ensuite passé à `COleDataSource::DoDragDrop` pour modifier le comportement par défaut de ces fonctions. Ces différentes options permettent de bénéficier d’une grande flexibilité dans la façon dont vous prenez en charge les opérations de glisser-déplacer dans votre application. Pour plus d’informations sur les sources de données, consultez l’article [objets de données et sources de données (OLE)](data-objects-and-data-sources-ole.md).

Vous pouvez substituer les fonctions suivantes pour personnaliser les opérations de glisser-déplacer :

| Écraser | Pour personnaliser |
| -------- | ------------ |
| `OnBeginDrag` | Comment l’opération glisser commence après l’appel de `DoDragDrop` . |
| `GiveFeedback` | Commentaires visuels, tels que l’apparence du curseur, pour différents résultats de dépôt. |
| `QueryContinueDrag` | Fin d’une opération de glisser-déplacer. Cette fonction vous permet de vérifier les États des touches de modification pendant l’opération glisser. |

## <a name="see-also"></a>Voir aussi

[ActiveX](ole-in-mfc.md)\
[Objets de données OLE et sources de données](data-objects-and-data-sources-ole.md)\
[Objets de données OLE et sources de données : création et destruction](data-objects-and-data-sources-creation-and-destruction.md)\
[Objets de données OLE et sources de données : manipulation](data-objects-and-data-sources-manipulation.md)\
[COleClientItem ::D oDragDrop](reference/coleclientitem-class.md#dodragdrop)\
[COleDataSource, classe](reference/coledatasource-class.md)\
[COleDataSource ::D oDragDrop](reference/coledatasource-class.md#dodragdrop)\
[COleDropSource, classe](reference/coledropsource-class.md)\
[COleDropTarget, classe](reference/coledroptarget-class.md)\
[CView :: OnDragLeave](reference/cview-class.md#ondragleave)
