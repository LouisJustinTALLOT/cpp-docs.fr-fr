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
ms.openlocfilehash: 530b1772dfb623689facd5b14eebe9ed1eacd4fd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624143"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Classes de glisser-déplacer OLE et de transfert de données

Ces classes sont utilisées dans les transferts de données OLE. Elles autorisent le transfert des données entre les applications à l’aide du presse-papiers ou par glisser-déplacer.

[COleDropSource](reference/coledropsource-class.md)<br/>
Contrôle l’opération de glisser-déplacer du début à la fin. Cette classe détermine le moment où l’opération glisser commence et le moment où elle se termine. Il affiche également les commentaires du curseur pendant l’opération de glisser-déplacer.

[COleDataSource](reference/coledatasource-class.md)<br/>
Utilisé lorsqu’une application fournit des données pour un transfert de données. `COleDataSource`peut être affiché en tant qu’objet de presse-papiers orienté objet.

[COleDropTarget](reference/coledroptarget-class.md)<br/>
Représente la cible d’une opération de glisser-déplacer. Un `COleDropTarget` objet correspond à une fenêtre à l’écran. Il détermine s’il faut accepter toutes les données déposées sur celui-ci et implémente l’opération de suppression réelle.

[COleDataObject](reference/coledataobject-class.md)<br/>
Utilisé comme côté récepteur `COleDataSource` . `COleDataObject`les objets fournissent l’accès aux données stockées par un `COleDataSource` objet.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
