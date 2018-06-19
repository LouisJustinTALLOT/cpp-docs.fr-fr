---
title: Création d’un fournisseur en lecture seule Simple | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2662a071f443967b921c4a8db27713bc7c3e8bb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096936"
---
# <a name="creating-a-simple-read-only-provider"></a>Création d'un fournisseur simple accessible en lecture seule
Lorsque vous avez créé un fournisseur OLE DB à l’aide de l’Assistant Projet ATL et l’Assistant fournisseur OLE DB ATL, vous pouvez ajouter d’autres fonctionnalités que vous souhaitez prendre en charge. Commencer à concevoir votre fournisseur en examinant le type de données que vous enverrez au consommateur et dans quelles conditions. Il est particulièrement important de déterminer si vous avez besoin prendre en charge les commandes, les transactions et les autres objets facultatifs. Une bonne conception en amont accélérer la mise en œuvre et test.  
  
 L’exemple est présenté en deux parties :  
  
-   La première partie montre comment [créer un fournisseur en lecture seule simple](../../data/oledb/implementing-the-simple-read-only-provider.md) qui lit une paire de chaînes.  
  
-   La seconde partie montre comment [améliorer le fournisseur simple en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md) en ajoutant le `IRowsetLocate` interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)