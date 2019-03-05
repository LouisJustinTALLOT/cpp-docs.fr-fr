---
title: Objets de données et sources de données (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
ms.openlocfilehash: 485fa5c62aafa4c116a76547238325d2979bfdc4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298267"
---
# <a name="data-objects-and-data-sources-ole"></a>Objets de données et sources de données (OLE)

Lorsque vous effectuez un transfert de données à l’aide du Presse-papiers ou glisser -déplacer, les données ont une source et une destination. Une application fournit les données pour la copie et une autre application accepte de collage. Chaque côté du transfert a besoin effectuer diverses opérations sur les mêmes données pour le transfert réussisse. La bibliothèque Microsoft Foundation classes (MFC) fournit deux classes qui représentent chaque côté de ce transfert :

- Sources de données (tel qu’implémenté par `COleDataSource` objets) représentent le côté source du transfert de données. Ils sont créés par l’application source lorsque les données ne doivent être copiés dans le Presse-papiers, ou lorsque les données sont fournies pour une opération de glisser-déplacer.

- Objets de données (tel qu’implémenté par `COleDataObject` objets) représentent le côté destination du transfert de données. Ils sont créés lors de l’application de destination a des données déplacées dans celui-ci, ou lorsqu’il est invité à effectuer une opération de collage à partir du Presse-papiers.

Les articles suivants expliquent comment utiliser des objets de données et sources de données dans vos applications. Ces informations s’appliquent aux applications de conteneur et le serveur, car les deux peuvent être appelés à copier et coller des données.

- [Objets de données et Sources de données : Création et Destruction](../mfc/data-objects-and-data-sources-creation-and-destruction.md)

- [Objets de données et Sources de données : Manipulation](../mfc/data-objects-and-data-sources-manipulation.md)

## <a name="in-this-section"></a>Dans cette section

[Glisser-déposer](../mfc/drag-and-drop-ole.md)

[Presse-papiers](../mfc/clipboard.md)

## <a name="see-also"></a>Voir aussi

[OLE](../mfc/ole-in-mfc.md)<br/>
[COleDataObject, classe](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource, classe](../mfc/reference/coledatasource-class.md)
