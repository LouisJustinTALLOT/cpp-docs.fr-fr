---
title: Sources de données et sessions
ms.date: 11/19/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: 0514f6a9285936c85608f08774c1d377fd72d6ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211053"
---
# <a name="data-sources-and-sessions"></a>Sources de données et sessions

L’illustration suivante montre les classes qui prennent en charge la connexion à une source de données et l’accès à celle-ci. Chaque classe est basée sur une implémentation de composant OLE DB standard.

![Classes de source de données et de session](../../data/oledb/media/vcdatasourcesessionclasses.gif "Classes de source de données et de session") <br/>
Classes de source de données et de session

Les classes sont les suivantes :

- [CDataSource](../../data/oledb/cdatasource-class.md) Cette classe instancie l’objet source de données, qui crée et gère une connexion à une source de données via un fournisseur OLE DB. La source de données prend des informations telles que l’adresse de la source de données et les informations d’authentification sous la forme d’une chaîne de connexion.

   Il est également intéressant de noter que la classe d’assistance [CEnumerator](../../data/oledb/cenumerator-class.md) est souvent utilisée avant l’établissement d’une connexion afin d’obtenir la liste des fournisseurs disponibles inscrits sur un système. Cela vous permet de sélectionner un fournisseur comme source de données. Par exemple, la boîte de dialogue **Propriétés des liaisons de données** utilise cette classe pour remplir la liste des fournisseurs sous l’onglet **fournisseurs** . Elle équivaut à la fonction `SQLBrowseConnect` ou `SQLDriverConnect`.

- [CSession](../../data/oledb/csession-class.md) Cette classe instancie l’objet de session, qui représente une session d’accès unique à la source de données. Toutefois, vous pouvez créer plusieurs sessions sur une source de données. Pour chaque session, vous pouvez créer des ensembles de lignes, des commandes et d’autres objets pour accéder aux données de la source de données. La session gère les transactions.

## <a name="see-also"></a>Voir aussi

[OLE DB (modèles du consommateur)](../../data/oledb/ole-db-consumer-templates-cpp.md)
