---
title: Commandes et tables
ms.date: 11/19/2018
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
ms.openlocfilehash: 0d5f6bd8d5f813497cba399e5c071f43dc1a7c4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211521"
---
# <a name="commands-and-tables"></a>Commandes et tables

Les commandes et les tables vous permettent d’accéder aux ensembles de lignes. autrement dit, les ensembles de lignes ouverts, les commandes d’exécution et les colonnes de liaison. Les classes [CCommand](../../data/oledb/ccommand-class.md) et [CTable](../../data/oledb/ctable-class.md) instancient respectivement la commande et les objets de table. Ces classes dérivent de [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) , comme indiqué dans l’illustration suivante.

![CCommand et CTable](../../data/oledb/media/vccommandstables.gif "CCommand et CTable")<br/>
Classes de commande et de table

Dans le tableau précédent, `TAccessor` peut être n’importe quel type d’accesseur listé dans les [types d’accesseurs](../../data/oledb/accessors-and-rowsets.md). `TRowset` peut être n’importe quel type d’ensemble de lignes listé dans [types d’ensembles de lignes](../../data/oledb/accessors-and-rowsets.md). `TMultiple` spécifie le type de résultat (un seul ou plusieurs jeux de résultats).

L' [Assistant consommateur d’OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) vous permet de spécifier si vous souhaitez une commande ou un objet de table.

- Pour les sources de données sans commandes, vous pouvez utiliser la classe `CTable`. Vous l’utilisez généralement pour des ensembles de lignes simples qui ne spécifient aucun paramètre et ne nécessitent pas de résultats multiples. Cette classe simple ouvre une table sur une source de données à l’aide d’un nom de table que vous spécifiez.

- Pour les sources de données qui prennent en charge les commandes, vous pouvez utiliser la classe `CCommand` à la place. Pour exécuter une commande, appelez [Open](../../data/oledb/ccommand-open.md) sur cette classe. Vous pouvez également appeler `Prepare` pour préparer une commande que vous souhaitez exécuter plusieurs fois.

   `CCommand` a trois arguments template : un type d’accesseur, un type d’ensemble de lignes et un type de résultat (`CNoMultipleResults`, par défaut, ou `CMultipleResults`). Si vous spécifiez `CMultipleResults`, la classe `CCommand` prend en charge l’interface `IMultipleResults` et gère plusieurs ensembles de lignes. L’exemple [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) montre comment gérer plusieurs résultats.

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)
