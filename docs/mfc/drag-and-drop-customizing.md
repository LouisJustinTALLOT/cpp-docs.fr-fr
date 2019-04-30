---
title: 'Glisser -déplacer : Personnalisation'
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
ms.openlocfilehash: b4749f8d45c962f8b9217e4c6367538d3e6a3608
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405948"
---
# <a name="drag-and-drop-customizing"></a>Glisser -déplacer : Personnalisation

L’implémentation par défaut de la fonctionnalité de glisser-déplacer est suffisante pour la plupart des applications. Toutefois, certaines applications peuvent nécessiter que modifier ce comportement standard. Cet article explique les étapes nécessaires pour modifier ces valeurs par défaut. En outre, vous pouvez utiliser cette technique pour établir des applications qui ne prennent pas en charge les documents composés comme sources de déplacement.

Si vous personnalisez le comportement de glisser-déplacer OLE standard ou si vous disposez d’une application non-OLE, vous devez créer un `COleDataSource` objet destiné à contenir les données. Lorsque l’utilisateur commence une opération de glisser-déplacer, votre code doit appeler la `DoDragDrop` fonction à partir de cet objet au lieu d’à partir d’autres classes qui prennent en charge les opérations de glisser-déplacer.

Si vous le souhaitez, vous pouvez créer un `COleDropSource` objet pour contrôler le déplacement et de remplacer certaines de ses fonctions selon le type de comportement que vous souhaitez modifier. Cet objet de source de déplacement est ensuite passé à `COleDataSource::DoDragDrop` pour modifier le comportement par défaut de ces fonctions. Ces différentes options permettent une grande flexibilité dans la façon dont vous prennent en charge les opérations de glisser-déplacer dans votre application. Pour plus d’informations sur les sources de données, consultez l’article [objets de données et Sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md).

Vous pouvez remplacer les fonctions suivantes pour personnaliser les opérations de glisser-déplacer :

|Remplacer|Pour personnaliser|
|--------------|------------------|
|`OnBeginDrag`|Comment faire glisser est lancée une fois que vous appelez `DoDragDrop`.|
|`GiveFeedback`|Commentaires visuels, tels que de l’apparence du curseur, pour les différents résultats du déplacement.|
|`QueryContinueDrag`|L’arrêt d’une opération de glisser-déplacer. Cette fonction vous permet de vérifier les États clés de modificateur pendant l’opération de glisser.|

## <a name="see-also"></a>Voir aussi

[Glisser-déposer (OLE)](../mfc/drag-and-drop-ole.md)<br/>
[COleDropSource, classe](../mfc/reference/coledropsource-class.md)<br/>
[COleDataSource, classe](../mfc/reference/coledatasource-class.md)
