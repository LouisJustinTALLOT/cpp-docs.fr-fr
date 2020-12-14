---
description: 'En savoir plus sur : glisser-déplacer OLE et classes Transfert de données'
title: Classes de glisser-déplacer OLE et de transfert de données
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: ea19efd05fe4b85a5c0e2ff57412f7eb1d05fcfe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244106"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Classes de glisser-déplacer OLE et de transfert de données

Ces classes sont utilisées dans les transferts de données OLE. Elles autorisent le transfert des données entre les applications à l’aide du presse-papiers ou par glisser-déplacer.

[COleDropSource](reference/coledropsource-class.md)<br/>
Contrôle l’opération de glisser-déplacer du début à la fin. Cette classe détermine le moment où l’opération glisser commence et le moment où elle se termine. Il affiche également les commentaires du curseur pendant l’opération de glisser-déplacer.

[COleDataSource](reference/coledatasource-class.md)<br/>
Utilisé lorsqu’une application fournit des données pour un transfert de données. `COleDataSource` peut être affiché en tant qu’objet de presse-papiers orienté objet.

[COleDropTarget](reference/coledroptarget-class.md)<br/>
Représente la cible d’une opération de glisser-déplacer. Un `COleDropTarget` objet correspond à une fenêtre à l’écran. Il détermine s’il faut accepter toutes les données déposées sur celui-ci et implémente l’opération de suppression réelle.

[COleDataObject](reference/coledataobject-class.md)<br/>
Utilisé comme côté récepteur `COleDataSource` . `COleDataObject` les objets fournissent l’accès aux données stockées par un `COleDataSource` objet.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
