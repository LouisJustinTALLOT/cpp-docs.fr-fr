---
title: Sources de données et sessions
ms.date: 10/22/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: 04b274677d98f1a544bcc190ce7155c00c4ee8d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650326"
---
# <a name="data-sources-and-sessions"></a>Sources de données et sessions

La figure suivante montre les classes qui prennent en charge la connexion et l’accès à une source de données. Chaque classe est basée sur une implémentation de composant OLE DB standard.

![Classes de données source et de la session](../../data/oledb/media/vcdatasourcesessionclasses.gif "vcdatasourcesessionclasses") Source de données et les Classes de Session

Les classes sont :

- [CDataSource](../../data/oledb/cdatasource-class.md) cette classe instancie l’objet de source de données, qui crée et gère une connexion à une source de données via un fournisseur OLE DB. La source de données accepte des informations telles que les informations source de données adresse et d’authentification sous la forme d’une chaîne de connexion.

   Il est également important de souligner que la classe d’assistance [CEnumerator](../../data/oledb/cenumerator-class.md) est souvent utilisée avant toute connexion est établie pour obtenir une liste des fournisseurs disponibles inscrits sur le système. Cela vous permet de sélectionner un fournisseur comme une source de données. Par exemple, le **propriétés des liaisons de données** boîte de dialogue utilise cette classe pour remplir la liste des fournisseurs sur le **fournisseurs** onglet. Il équivaut à la `SQLBrowseConnect` ou `SQLDriverConnect` (fonction).

- [CSession](../../data/oledb/csession-class.md) cette classe instancie l’objet de session, qui représente une session d’accès unique à la source de données. Toutefois, vous pouvez créer plusieurs sessions sur une source de données. Pour chaque session, vous pouvez créer des ensembles de lignes, commandes et d’autres objets pour accéder aux données à partir de la source de données. La session gère des transactions.

## <a name="see-also"></a>Voir aussi

[Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)