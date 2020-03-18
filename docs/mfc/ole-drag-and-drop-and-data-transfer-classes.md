---
title: Classes de glisser-déplacer OLE et de transfert de données
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 7e01b6d5a7d14e0af4ca760e6e601e91359c8ab1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447613"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Classes de glisser-déplacer OLE et de transfert de données

Ces classes sont utilisées dans les transferts de données OLE. Elles autorisent le transfert des données entre les applications à l’aide du presse-papiers ou par glisser-déplacer.

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
Contrôle l’opération de glisser-déplacer du début à la fin. Cette classe détermine le moment où l’opération glisser commence et le moment où elle se termine. Il affiche également les commentaires du curseur pendant l’opération de glisser-déplacer.

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
Utilisé lorsqu’une application fournit des données pour un transfert de données. `COleDataSource` peut être affiché en tant qu’objet de presse-papiers orienté objet.

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
Représente la cible d’une opération de glisser-déplacer. Un objet `COleDropTarget` correspond à une fenêtre à l’écran. Il détermine s’il faut accepter toutes les données déposées sur celui-ci et implémente l’opération de suppression réelle.

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
Utilisé comme côté récepteur pour `COleDataSource`. les objets `COleDataObject` fournissent l’accès aux données stockées par un objet `COleDataSource`.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
