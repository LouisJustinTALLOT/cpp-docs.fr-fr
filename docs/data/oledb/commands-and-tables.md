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
ms.openlocfilehash: b2cdf7a2b439af3a564f5801e015f6064fb141dc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041414"
---
# <a name="commands-and-tables"></a>Commandes et tables

Commandes et tables pouvoir accéder aux ensembles de lignes ; Autrement dit, ouvrir des ensembles de lignes, exécuter des commandes et lier les colonnes. Le [CCommand](../../data/oledb/ccommand-class.md) et [CTable](../../data/oledb/ctable-class.md) classes instancient les objets de commande et de table, respectivement. Ces classes dérivent [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) comme indiqué dans l’illustration suivante.

![CCommand et CTable](../../data/oledb/media/vccommandstables.gif "CCommand et CTable")<br/>
Commande et les Classes de Table

Dans le tableau précédent, `TAccessor` peut être n’importe quel type d’accesseur répertoriée dans [Types d’accesseurs](../../data/oledb/accessors-and-rowsets.md). `TRowset` peut être n’importe quel type d’ensemble de lignes répertoriée dans [Types de l’ensemble de lignes](../../data/oledb/accessors-and-rowsets.md). `TMultiple` Spécifie le type de résultat (un seul ou plusieurs de jeu de résultats).

Le [Assistant Consommateur OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) vous permet de spécifier si un objet de commande ou de table.

- Pour les sources de données sans les commandes, vous pouvez utiliser la `CTable` classe. Vous l’utilisez généralement pour des ensembles de lignes simples qui ne spécifiez aucun paramètre et ne nécessitent aucune plusieurs résultats. Cette classe simple ouvre une table sur une source de données à l’aide d’un nom de table que vous spécifiez.

- Pour les sources de données qui prennent en charge les commandes, vous pouvez utiliser la `CCommand` classe à la place. Pour exécuter une commande, appelez [Open](../../data/oledb/ccommand-open.md) sur cette classe. Comme alternative, vous pouvez appeler `Prepare` pour préparer une commande que vous souhaitez exécuter plusieurs fois.

   `CCommand` possède trois arguments template : un type d’accesseur, un type d’ensemble de lignes et un type de résultat (`CNoMultipleResults`, par défaut, ou `CMultipleResults`). Si vous spécifiez `CMultipleResults`, le `CCommand` classe prend en charge la `IMultipleResults` interface et gère plusieurs ensembles de lignes. Le [DBVIEWER](https://github.com/Microsoft/VCSamples) exemple montre comment gérer les résultats multiples.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)