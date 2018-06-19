---
title: 'Glisser -déplacer : personnalisation | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [MFC], implementing in non-OLE applications
- drag and drop [MFC], customizing behavior
- drag and  [MFC], COleDataSource object
- drag and drop [MFC], calling DoDragDrop
- OLE drag and drop [MFC], customizing behavior
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59ec5a5a493106750fa7bb8c7ec31b8dbb011070
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344241"
---
# <a name="drag-and-drop-customizing"></a>Glisser-déposer : personnalisation
L’implémentation par défaut de la fonctionnalité de glisser-déplacer est suffisante pour la plupart des applications. Toutefois, certaines applications peuvent nécessiter que ce comportement par défaut est modifié. Cet article explique les étapes nécessaires pour modifier ces valeurs par défaut. En outre, vous pouvez utiliser cette technique pour établir des applications qui ne prennent pas en charge les documents composés comme sources de déplacement.  
  
 Si vous personnalisez le comportement de glisser-déplacer OLE standard ou si vous avez une application non-OLE, vous devez créer un `COleDataSource` objet pour contenir les données. Lorsque l’utilisateur commence une opération de glisser-déplacer, votre code doit appeler la `DoDragDrop` fonction à partir de cet objet plutôt qu’à partir d’autres classes qui prennent en charge les opérations de glisser-déplacer.  
  
 Si vous le souhaitez, vous pouvez créer un `COleDropSource` objet pour contrôler le déplacement et substituer certaines de ses fonctions selon le type de comportement que vous souhaitez modifier. Cet objet de source de déplacement est ensuite passé à `COleDataSource::DoDragDrop` pour modifier le comportement par défaut de ces fonctions. Ces différentes options permettent une grande souplesse dans la façon dont vous prennent en charge les opérations de glisser-déplacer dans votre application. Pour plus d’informations sur les sources de données, consultez l’article [des objets de données et Sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Vous pouvez substituer les fonctions suivantes pour personnaliser les opérations de glisser-déplacer :  
  
|Remplacer|Pour personnaliser|  
|--------------|------------------|  
|`OnBeginDrag`|Comment le glissement est lancé après l’appel de `DoDragDrop`.|  
|`GiveFeedback`|Retour visuel, tels que de l’apparence du curseur, pour les différents résultats du déplacement.|  
|`QueryContinueDrag`|L’arrêt d’une opération de glisser-déplacer. Cette fonction permet de vérifier les États de clés de modificateur pendant l’opération de glissement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Glisser -déplacer (OLE)](../mfc/drag-and-drop-ole.md)   
 [Classe de COleDropSource](../mfc/reference/coledropsource-class.md)   
 [COleDataSource, classe](../mfc/reference/coledatasource-class.md)
