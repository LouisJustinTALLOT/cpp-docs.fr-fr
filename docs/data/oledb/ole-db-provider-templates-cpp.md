---
description: En savoir plus sur les modèles de fournisseur OLE DB (C++)
title: Modèles du fournisseur OLE DB (C++)
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
ms.openlocfilehash: 8706fcd9467e6d184633917d7c83ac81ad137b9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286915"
---
# <a name="ole-db-provider-templates-c"></a>Modèles du fournisseur OLE DB (C++)

OLE DB est une partie importante de la stratégie Microsoft Universal Data Access. La conception OLE DB permet l’accès aux données à hautes performances à partir de n’importe quelle source de données. Toutes les données tabulaires sont consultables par OLE DB qu’elles proviennent d’une base de données ou non. La flexibilité vous offre une énorme puissance.

Comme expliqué dans [OLE DB consommateurs et fournisseurs](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB utilise le concept de consommateurs et de fournisseurs. Le consommateur effectue des demandes de données ; le fournisseur retourne des données dans un format tabulaire au consommateur. Du point de vue de la programmation, l’implication la plus importante de ce modèle est que le fournisseur doit implémenter n’importe quel appel que le consommateur peut effectuer.

## <a name="what-is-a-provider"></a>Qu’est-ce qu’un fournisseur ?

Un fournisseur de OLE DB est un ensemble d’objets COM qui traitent des appels d’interface à partir d’un objet de consommateur, en transférant les données dans un format tabulaire à partir d’une source durable (appelée magasin de données) vers le consommateur.

Les fournisseurs peuvent être simples ou complexes. Le fournisseur peut prendre en charge une quantité minimale de fonctionnalités ou un fournisseur de qualité de production complet en implémentant davantage d’interfaces. Un fournisseur peut retourner une table, autoriser le client à déterminer le format de cette table et effectuer des opérations sur ces données.

Chaque fournisseur implémente un ensemble standard d’objets COM pour gérer les demandes du client, avec une signification standard que tout OLE DB consommateur peut accéder aux données de n’importe quel fournisseur, quel que soit le langage (C++ et de base, par exemple).

Chaque objet COM contient plusieurs interfaces, dont certaines sont obligatoires et dont certaines sont facultatives. En implémentant les interfaces obligatoires, un fournisseur garantit un niveau de fonctionnalité minimal (appelé « conformité ») que n’importe quel client doit pouvoir utiliser. Un fournisseur peut implémenter des interfaces facultatives pour fournir des fonctionnalités supplémentaires. L' [architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md) décrit ces interfaces en détail. Le client doit toujours appeler `QueryInterface` pour déterminer si un fournisseur prend en charge une interface donnée.

## <a name="ole-db-specification-level-support"></a>Prise en charge du niveau de spécification OLE DB

Les modèles du fournisseur OLE DB prennent en charge la spécification OLE DB version 2,7. À l’aide des modèles de fournisseur OLE DB, vous pouvez implémenter un fournisseur de compatibilité de niveau 0. L' `Provider` exemple utilise, par exemple, les modèles pour implémenter un serveur de commandes non-SQL (MS-DOS) qui exécute la commande DOS dir pour interroger le système de fichiers. L' `Provider` exemple retourne les informations de répertoire dans un ensemble de lignes, qui est le mécanisme de OLE DB standard pour retourner des données sous forme de tableau.

Le type de fournisseur le plus simple pris en charge par les modèles OLE DB est un fournisseur en lecture seule sans commande. Les fournisseurs avec des commandes sont également pris en charge, tout comme les fonctionnalités de signet et de lecture/écriture. Vous pouvez implémenter un fournisseur de lecture/écriture en écrivant du code supplémentaire. Les ensembles de lignes dynamiques et les transactions ne sont pas pris en charge par la version actuelle, mais vous pouvez les ajouter si vous le souhaitez.

## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>Quand avez-vous besoin de créer un fournisseur de OLE DB ?

Vous n’avez pas toujours besoin de créer votre propre fournisseur. Microsoft fournit plusieurs fournisseurs standard préemballés dans la boîte de dialogue **Propriétés des liaisons de données** de Visual C++. La principale raison de créer un fournisseur de OLE DB est de tirer parti de la stratégie d’accès universel aux données. Voici quelques-uns des avantages :

- Accès aux données par le biais de n’importe quel langage, tel que C++, Basic et Visual Basic Scripting Edition. Il permet à différents programmeurs de votre organisation d’accéder aux mêmes données de la même manière, quelle que soit la langue utilisée.

- Ouvrez vos données dans d’autres sources de données, telles que SQL Server, Excel et Access. Cela peut être utile si vous souhaitez transférer des données entre différents formats.

- Participer à des opérations de sources de données croisées (hétérogènes). Cela peut être un moyen efficace d’entreposage des données. En utilisant des fournisseurs de OLE DB, vous pouvez conserver les données dans leur format natif et toujours y accéder dans une opération simple.

- Ajout de fonctionnalités supplémentaires à vos données, telles que le traitement des requêtes.

- Amélioration des performances d’accès aux données en contrôlant la façon dont elles sont manipulées.

- Robustesse accrue. Si vous disposez d’un format de données propriétaire auquel un seul programmeur peut accéder, vous êtes menacé. À l’aide des fournisseurs de OLE DB, vous pouvez ouvrir ce format propriétaire pour tous vos programmeurs.

## <a name="read-only-and-updatable-providers"></a>Fournisseurs Read-Only et pouvant être mis à jour

Les fournisseurs peuvent varier considérablement en matière de complexité et de fonctionnalité. Il est utile de catégoriser les fournisseurs en fournisseurs en lecture seule et en fournisseurs pouvant être mis à jour :

- Visual C++ 6,0 ne prenait en charge que les fournisseurs en lecture seule. La [création d’un fournisseur de OLE DB](../../data/oledb/creating-an-ole-db-provider.md) explique comment créer un fournisseur en lecture seule.
- Visual C++ prend en charge les fournisseurs pouvant être mis à jour, qui peuvent mettre à jour (écrire dans) le magasin de données. Pour plus d’informations sur les fournisseurs pouvant être mis à jour, consultez [création d’un fournisseur pouvant être mis à jour](../../data/oledb/creating-an-updatable-provider.md); l’exemple [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) est un exemple de fournisseur pouvant être mis à jour.

Pour plus d'informations, consultez les pages suivantes :

- [Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)

- [Création d’un fournisseur de OLE DB](../../data/oledb/creating-an-ole-db-provider.md)

- [Programmation OLE DB](../../data/oledb/ole-db-programming.md)

## <a name="see-also"></a>Voir aussi

[Accès aux données](../data-access-in-cpp.md)<br/>
[Documentation du Kit de développement logiciel (SDK) OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[Informations de référence du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)<br/>
