---
title: Objets de données et Sources de données (OLE) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data objects [MFC], definition
- data transfer [MFC]
- OLE [MFC], data transfer
- data sources [MFC], definition
- data transfer [MFC], definition
- OLE [MFC], data objects
- OLE [MFC], data sources
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 766148494c6b8693f8d9e65f27e157b58d8e8689
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342977"
---
# <a name="data-objects-and-data-sources-ole"></a>Objets de données et sources de données (OLE)
Lorsque vous effectuez un transfert de données, à l’aide du Presse-papiers ou de glisser -déplacer, les données ont une source et une destination. Une application fournit les données pour la copie et une autre application accepte de collage. Chaque côté du transfert a besoin effectuer diverses opérations sur les mêmes données pour le transfert réussisse. La bibliothèque Microsoft Foundation classes (MFC) fournit deux classes qui représentent chaque côté de ce transfert :  
  
-   Sources de données (tel qu’implémenté par `COleDataSource` objets) représentent le côté source du transfert de données. Ils sont créés par l’application source lorsque les données sont à copier dans le Presse-papiers, ou lorsque les données sont fournies pour une opération de glisser-déplacer.  
  
-   Objets de données (tel qu’implémenté par `COleDataObject` objets) représentent le côté destination du transfert de données. Ils sont créés lors de l’application de destination comporte des données supprimées dans celui-ci, ou lorsqu’il est invité à effectuer une opération de collage à partir du Presse-papiers.  
  
 Les articles suivants expliquent comment utiliser des objets de données et sources de données dans vos applications. Ces informations s’appliquent aux applications conteneur et serveur, car les deux peuvent être appelés pour copier et coller des données.  
  
-   [Objets de données et sources de données : création et destruction](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Objets de données et sources de données : manipulation](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="in-this-section"></a>Dans cette section  
 [Glisser-déposer](../mfc/drag-and-drop-ole.md)  
  
 [Presse-papiers](../mfc/clipboard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OLE](../mfc/ole-in-mfc.md)   
 [Classe de COleDataObject](../mfc/reference/coledataobject-class.md)   
 [COleDataSource, classe](../mfc/reference/coledatasource-class.md)
