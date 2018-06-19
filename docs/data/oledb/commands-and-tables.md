---
title: Commandes et Tables | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, table support
- CCommand class, OLE DB consumer templates
- commands [C++], OLE DB Consumer Templates
- CTable class
- CAccessorRowset class, command and table classes
- rowsets, accessing
- tables [C++], OLE DB Consumer Templates
- OLE DB consumer templates, command support
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 23d2739807a065b93b10a209a9ea68070b36970b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098678"
---
# <a name="commands-and-tables"></a>Commandes et tables
Commandes et tables permettent d’accéder aux ensembles de lignes ; Autrement dit, ouvrir des ensembles de lignes, exécuter des commandes et lier les colonnes. Le [CCommand](../../data/oledb/ccommand-class.md) et [CTable](../../data/oledb/ctable-class.md) classes instancient les objets de commande et de table, respectivement. Ces classes dérivent [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) comme indiqué dans l’illustration suivante.  
  
 ![CCommand et CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")  
Les Classes de Table et de commande  
  
 Dans le tableau précédent, `TAccessor` peut être n’importe quel type d’accesseur répertorié dans [Types d’accesseurs](../../data/oledb/accessors-and-rowsets.md). *TRowset* peut être n’importe quel type d’ensemble de lignes répertoriée dans [Types de l’ensemble de lignes](../../data/oledb/accessors-and-rowsets.md). *TMultiple* Spécifie le type de résultat (un seul ou plusieurs de jeu de résultats).  
  
 Le [Assistant Consommateur OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) vous permet de spécifier si un objet de commande ou de table.  
  
-   Pour les sources de données sans les commandes, vous pouvez utiliser la `CTable` classe. Vous l’utilisez généralement pour les ensembles de lignes simples qui ne spécifiez aucun paramètre et exigent aucun résultat multiple. Cette classe simple ouvre une table sur une source de données à l’aide d’un nom de table que vous spécifiez.  
  
-   Pour les sources de données qui prennent en charge les commandes, vous pouvez utiliser la `CCommand` classe à la place. Pour exécuter une commande, appelez [ouvrir](../../data/oledb/ccommand-open.md) sur cette classe. En guise d’alternative, vous pouvez appeler `Prepare` pour préparer une commande que vous souhaitez exécuter plusieurs fois.  
  
     **CCommand** possède trois arguments template : un type d’accesseur, un type d’ensemble de lignes et un type de résultat (`CNoMultipleResults`, par défaut, ou `CMultipleResults`). Si vous spécifiez `CMultipleResults`, le `CCommand` classe prend en charge la **IMultipleResults** interface et gère plusieurs ensembles de lignes. Le [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) montre comment gérer les résultats multiples.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)