---
title: Classes de glisser-déposer OLE et de transfert de données
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 7520881314da9568f6130f5fe2ccf0a3e0e88e2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475180"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Classes de glisser-déposer OLE et de transfert de données

Ces classes sont utilisées dans les transferts de données OLE. Ils permettent aux données à transférer entre applications en utilisant le Presse-papiers ou par glisser-déplacer.

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
Contrôle de l’opération de glisser-déplacer à partir du début à la fin. Cette classe détermine quand l’opération glisser commence et lorsqu’elle se termine. Elle affiche également le commentaire du curseur pendant l’opération de glisser-déplacer.

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
Utilisé lorsqu’une application fournit des données pour un transfert de données. `COleDataSource` peut être considéré comme un objet Clipboard et orienté objet.

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
Représente la cible d’une opération de glisser-déplacer. Un `COleDropTarget` objet correspond à une fenêtre sur l’écran. Il détermine s’il faut accepter toutes les données déposés sur lui et implémentant l’opération de déplacement réel.

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
Utilisé en tant que le côté récepteur à `COleDataSource`. `COleDataObject` objets de fournissent un accès aux données stockées par une `COleDataSource` objet.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

