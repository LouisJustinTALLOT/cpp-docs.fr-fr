---
title: Modèles du fournisseur OLE DB (C++)
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
ms.openlocfilehash: c88e03f509da3c97c270e308dc6dd44e3b44aeb7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413782"
---
# <a name="ole-db-provider-templates-c"></a>Modèles du fournisseur OLE DB (C++)

OLE DB est une partie importante de la stratégie Microsoft Universal Data Access. L’architecture OLE DB autorise l’accès de données hautes performances à partir de n’importe quelle source de données. Les données tabulaires sont accessibles via OLE DB, qu’elles proviennent d’une base de données. La flexibilité vous donne une énorme quantité d’énergie.

Comme expliqué dans [fournisseurs et consommateurs OLE DB](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB utilise le concept de fournisseurs et consommateurs. Le consommateur présente des demandes de données ; le fournisseur retourne des données dans un format tabulaire au consommateur. Du point de vue de la programmation, l’implication la plus importante de ce modèle est que le fournisseur doit implémenter n’importe quel appel qu'au consommateur.

## <a name="what-is-a-provider"></a>Qu’est un fournisseur ?

Un fournisseur OLE DB est un ensemble d’objets COM qui servent d’interface appelle à partir d’un objet du consommateur, transfert de données dans un format tabulaire à partir d’une source fiable (appelée magasin de données) vers le consommateur.

Fournisseurs peuvent être simples ou complexes. Le fournisseur peut prendre en charge une quantité minimale de fonctionnalités ou d’un fournisseur de qualité de production complet en implémentant plusieurs interfaces. Un fournisseur peut retourner une table, permettre au client déterminer le format de la table et effectuer des opérations sur ces données.

Chaque fournisseur implémente un jeu standard d’objets COM pour gérer les demandes du client, avec une signification standard que tout consommateur OLE DB peut accéder aux données à partir de n’importe quel fournisseur, quel que soit le langage (tels que C++ et de base).

Chaque objet COM contient plusieurs interfaces, certains d'entre eux sont requis et certains d'entre eux sont facultatifs. En implémentant les interfaces obligatoires, un fournisseur garantit un niveau minimal de fonctionnalités (appelé conformité) qui n’importe quel client doit être en mesure d’utiliser. Un fournisseur peut implémenter des interfaces facultatives pour fournir des fonctionnalités supplémentaires. Le [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md) décrit ces interfaces en détail. Le client doit toujours appeler `QueryInterface` pour déterminer si un fournisseur prend en charge une interface donnée.

## <a name="ole-db-specification-level-support"></a>Prise en charge du niveau de la spécification OLE DB

Les modèles du fournisseur OLE DB prend en charge la spécification OLE DB version 2.7. À l’aide des modèles du fournisseur OLE DB, vous pouvez implémenter un fournisseur conforme au niveau 0. Le `Provider` , par exemple, utilise les modèles pour implémenter un serveur de commande non-MS-DOS qui exécute la commande DOS DIR pour interroger le système de fichiers. Le `Provider` exemple retourne les informations d’annuaire dans un ensemble de lignes, ce qui est le mécanisme OLE DB standard pour retourner des données tabulaires.

Le type le plus simple de fournisseur pris en charge par les modèles OLE DB est un fournisseur en lecture seule sans commande. Fournisseurs avec les commandes sont également prises en charge, sont des fonctionnalités de création de signets et en lecture/écriture. Vous pouvez implémenter un fournisseur de lecture/écriture en écrivant du code supplémentaire. Transactions et les ensembles de lignes dynamiques ne sont pas pris en charge par la version actuelle, mais vous pouvez les ajouter si vous le souhaitez.

## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>Lorsque vous avez besoin créer un fournisseur OLE DB ?

Vous n’avez pas toujours besoin créer votre propre fournisseur ; Microsoft propose plusieurs fournisseurs prépackagés, standards dans le **propriétés des liaisons de données** boîte de dialogue dans Visual C++. La principale raison de créer un fournisseur OLE DB consiste à tirer parti de la stratégie d’accès aux données universel. Certains des avantages de cette opération sont donc :

- L’accès aux données via n’importe quel langage, tels que C++, Basic et Visual Basic Scripting Edition. Il permet aux programmeurs de différents dans votre organisation pour accéder aux mêmes données de la même façon, quel que soit de langage qu’ils utilisent.

- Ouvrez vos données vers d’autres sources de données telles que SQL Server, Excel et Access. Cela peut être utile si vous souhaitez transférer des données entre différents formats.

- Participe aux opérations de source de données croisées (hétérogènes). Cela peut être un moyen efficace d’entreposage de données. À l’aide de fournisseurs OLE DB, vous pouvez conserver les données dans son format natif et toujours être en mesure d’y accéder dans une opération simple.

- Ajout de fonctionnalités supplémentaires à vos données, telles que le traitement de requête.

- Accroître les performances de l’accès aux données en contrôlant la façon dont il est manipulé.

- Amélioration de la robustesse. Si vous avez un format de données propriétaires ce qu’un programmeur peut accéder, vous êtes en danger. À l’aide de fournisseurs OLE DB, vous pouvez ouvrir ce format propriétaire à tous vos programmeurs.

## <a name="read-only-and-updatable-providers"></a>Fournisseurs en lecture seule et être mise à jour

Fournisseurs peuvent varier considérablement la complexité et de fonctionnalités. Il est utile de classer les fournisseurs dans les fournisseurs en lecture seule et être mise à jour :

- Visual C++ 6.0 pris en charge uniquement les fournisseurs en lecture seule. [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md) explique comment créer un fournisseur en lecture seule.
- Visual C++ prend en charge les fournisseurs actualisables, qui peuvent mettre à jour (modifier) le magasin de données. Pour plus d’informations sur les fournisseurs d’être mise à jour, consultez [création d’un fournisseur actualisable](../../data/oledb/creating-an-updatable-provider.md); le [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) est un exemple d’un fournisseur actualisable.

Pour plus d'informations, voir :

- [L’Architecture de modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)

- [Création d’un fournisseur OLE DB](../../data/oledb/creating-an-ole-db-provider.md)

- [Programmation OLE DB](../../data/oledb/ole-db-programming.md)

## <a name="see-also"></a>Voir aussi

[Accès aux données](../data-access-in-cpp.md)<br/>
[Documentation du Kit de développement OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[Informations de référence du programmeur OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)<br/>
