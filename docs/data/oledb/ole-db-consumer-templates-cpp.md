---
title: Modèles du consommateur OLE DB (C++)
ms.date: 10/22/2018
helpviewer_keywords:
- databases [C++], OLE DB templates
- OLE DB consumers [C++], data access
- OLE DB consumer templates [C++]
- databases [C++], consumers
ms.assetid: d3e42612-0bc0-4d65-9c32-0e8a7b219e82
ms.openlocfilehash: f3b247660e65975630b9434685d0a12caf0fc257
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419168"
---
# <a name="ole-db-consumer-templates-c"></a>Modèles du consommateur OLE DB (C++)

Les modèles de consommateurs OLE DB prennent ne charge la spécification OLE DB version 2.6. (Les modèles du consommateur OLE DB sont testés pour OLE DB 2.6, mais ne prend pas en charge chaque interface dans la spécification.) Les modèles de consommateurs réduisent la quantité de code que vous devez écrire pour implémenter un consommateur OLE DB. Les modèles fournissent :

- Un accès facile aux fonctionnalités d’OLE DB, et une intégration facile à ATL et à MFC.

- Un modèle de liaison facile pour les paramètres et les colonnes des bases de données.

- Des types de données C/C++ natifs pour la programmation OLE DB.

Pour utiliser les modèles OLE DB, vous devez bien connaître les modèles C++, COM et les interfaces OLE DB. Si vous n’êtes pas familiarisé avec OLE DB, consultez [de référence du programmeur OLE DB](/previous-versions/windows/desktop/ms718124(v=vs.85)).

Les modèles OLE DB prennent en charge le modèle objet OLE DB existant, au lieu d’ajouter un nouveau modèle objet. Les classes de la couche la plus élevée des modèles de consommateur OLE DB figurent en parallèle des composants définis dans la spécification OLE DB. La conception des modèles de consommateur OLE DB comprend des fonctionnalités avancées, comme les accesseurs multiples sur un ensemble de lignes. L’utilisation de modèles et de l’héritage multiple rend la bibliothèque souple et d’une taille réduite.

## <a name="how-ole-db-consumers-access-data"></a>Comment les consommateurs OLE DB accèdent aux données

Les consommateurs utilisent différentes sortes d’objets, qui sont décrits dans les rubriques suivantes :

- [Sources de données et sessions](../../data/oledb/data-sources-and-sessions.md)

- [Accesseurs et jeux de lignes](../../data/oledb/accessors-and-rowsets.md)

- [Commandes et tables](../../data/oledb/commands-and-tables.md)

- [Enregistrements utilisateur](../../data/oledb/user-records.md)

Avant que le consommateur fasse quoi que ce soit, vous devez d’abord sélectionner un fournisseur OLE DB approprié au type de la base de données à laquelle vous devez accéder (par exemple SQL, Oracle, ODBC et MSDS). Pour cela, vous utilisez généralement un énumérateur (consultez [CEnumerator](../../data/oledb/cenumerator-class.md) comme mentionné dans [Sources de données et sessions](../../data/oledb/data-sources-and-sessions.md)).

L’ [objet de source de données](../../data/oledb/data-sources-and-sessions.md) fournit les informations de connexion nécessaires pour se connecter à la source de données que vous avez sélectionnée. L’objet source de données contient aussi des informations d’authentification (comme les noms et mots de passe de connexion), qui sont utilisées pour donner aux utilisateurs l’autorisation d’accéder à la source de données. L’objet source de données établit une connexion à la base de données, puis crée un ou plusieurs objets session. Chaque [objet de session](../../data/oledb/data-sources-and-sessions.md) gère ses propres interactions avec la base de données (effectuer des requêtes sur les données et les récupérer) et effectue ces transactions indépendamment des autres sessions existantes.

La session crée des objets ensemble de lignes et commande. L’ [objet de commande](../../data/oledb/commands-and-tables.md) permet aux utilisateurs d’interagir avec la base de données, par exemple en utilisant des commandes SQL. L’ [objet d’ensemble de lignes (rowset)](../../data/oledb/accessors-and-rowsets.md) est un ensemble de données à travers lequel vous pouvez naviguer et où vous pouvez [mettre à jour, supprimer et insérer des lignes](../../data/oledb/updating-rowsets.md).

Un consommateur OLE DB lie les colonnes des tables de la base de données à des variables locales. Pour cela, il utilise un [accesseur](../../data/oledb/accessors-and-rowsets.md), qui contient un mappage indiquant comment les données sont stockées dans le consommateur. Le mappage est constitué d’un ensemble de liaisons entre les colonnes des tables et les mémoires tampons (variables) locales de l’application consommatrice.

Un concept important pour travailler avec des consommateurs est que vous déclarez deux classes dans un consommateur : la [classe command (ou table)](../../data/oledb/commands-and-tables.md) et la [classe enregistrement utilisateur](../../data/oledb/user-records.md). Vous accédez à l’ensemble de lignes via la classe command (ou table), qui hérite à la fois d’une classe accessor et d’une classe rowset. La classe d’enregistrement utilisateur (user record) contient le mappage des liaisons de lignes décrit précédemment.

Pour plus d’informations, consultez les rubriques suivantes :

- [Création d’un consommateur OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)

- [Scénarios courants de consommateur OLE DB (exemples)](../../data/oledb/working-with-ole-db-consumer-templates.md)

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Accès aux données](../data-access-in-cpp.md)<br/>
[Documentation du Kit de développement OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[Informations de référence du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)
