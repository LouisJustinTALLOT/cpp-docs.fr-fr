---
description: 'En savoir plus sur : commandes et tables'
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
ms.openlocfilehash: 767077af7b44b4727272fefc1c2af2f717baddd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323338"
---
# <a name="commands-and-tables"></a>Commandes et tables

Les commandes et les tables vous permettent d’accéder aux ensembles de lignes. autrement dit, les ensembles de lignes ouverts, les commandes d’exécution et les colonnes de liaison. Les classes [CCommand](../../data/oledb/ccommand-class.md) et [CTable](../../data/oledb/ctable-class.md) instancient respectivement la commande et les objets de table. Ces classes dérivent de [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) , comme indiqué dans l’illustration suivante.

![CCommand et CTable](../../data/oledb/media/vccommandstables.gif "CCommand et CTable")<br/>
Classes de commande et de table

Dans le tableau précédent, `TAccessor` peut être n’importe quel type d’accesseur listé dans les [types d’accesseur](../../data/oledb/accessors-and-rowsets.md). `TRowset` peut être n’importe quel type d’ensemble de lignes listé dans les [types d’ensembles de lignes](../../data/oledb/accessors-and-rowsets.md). `TMultiple` Spécifie le type de résultat (un seul ou plusieurs jeux de résultats).

L' [Assistant consommateur d’OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) vous permet de spécifier si vous souhaitez une commande ou un objet de table.

- Pour les sources de données sans commandes, vous pouvez utiliser la `CTable` classe. Vous l’utilisez généralement pour des ensembles de lignes simples qui ne spécifient aucun paramètre et ne nécessitent pas de résultats multiples. Cette classe simple ouvre une table sur une source de données à l’aide d’un nom de table que vous spécifiez.

- Pour les sources de données qui prennent en charge les commandes, vous pouvez utiliser la classe à la `CCommand` place. Pour exécuter une commande, appelez [Open](./ccommand-class.md#open) sur cette classe. Vous pouvez également appeler `Prepare` pour préparer une commande que vous souhaitez exécuter plusieurs fois.

   `CCommand` a trois arguments template : un type d’accesseur, un type d’ensemble de lignes et un type de résultat ( `CNoMultipleResults` , par défaut, ou `CMultipleResults` ). Si vous spécifiez `CMultipleResults` , la `CCommand` classe prend en charge l' `IMultipleResults` interface et gère plusieurs ensembles de lignes. L’exemple [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) montre comment gérer plusieurs résultats.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)
