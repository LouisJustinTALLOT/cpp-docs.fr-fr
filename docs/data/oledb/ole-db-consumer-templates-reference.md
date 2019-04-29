---
title: Référence des modèles du consommateur OLE DB
ms.date: 11/04/2016
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: fb0b24798b3f2682bbbec7624df34b40a2a9f4cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361488"
---
# <a name="ole-db-consumer-templates-reference"></a>Référence des modèles du consommateur OLE DB

Les modèles du consommateur OLE DB contient les classes suivantes. La documentation de référence inclut également des rubriques sur la [macros pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="session-classes"></a>Classes de session

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
Gère la connexion avec la source de données. Il s’agit d’une classe utile pour la création de clients, car elle encapsule les objets nécessaires (source de données et session) et la partie du travail, que vous devez effectuer lors de la connexion à une source de données.

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
Correspond à un objet de source de données OLE DB, qui représente une connexion via un fournisseur de source de données. Un ou plusieurs sessions base de données, chacun est représenté par un `CSession` d’objets, peuvent avoir lieu sur une seule connexion.

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
Correspond à un objet énumérateur OLE DB, qui Récupère l’ensemble de lignes d’informations sur les sources de données disponibles.

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
Utilisé par `CEnumerator` pour accéder aux données à partir de l’ensemble de lignes d’énumérateur. Cet ensemble de lignes se compose des sources de données et des énumérateurs visibles à partir de l’énumérateur en cours.

[CSession](../../data/oledb/csession-class.md)<br/>
Représente une session d’accès de base de données unique. Une ou plusieurs sessions peuvent être associée à chaque `CDataSource` objet.

## <a name="accessor-classes"></a>Classes d’accesseurs

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
Utilisé pour les enregistrements qui sont liées statiquement à une source de données. Utilisez cette classe d’accesseur lorsque vous connaissez la structure de la source de données.

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
Classe de base pour toutes les classes d’accesseur.

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
Un accesseur qui peut être créé au moment de l’exécution, en fonction des informations de colonne de l’ensemble de lignes. Utilisez cette classe pour récupérer des données si vous ne connaissez pas la structure de la source de données.

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
Un accesseur qui peut être utilisé lorsque les types de commande sont inconnus. Obtient les informations de paramètre en appelant le `ICommandWithParameters` interface, si le fournisseur prend en charge l’interface.

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
Vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance de la structure sous-jacente de la base de données.

[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
Similaire à `CDynamicStringAccessor` , à ceci près que cette classe demande des données accédées à partir de la banque de données en tant que données de chaîne ANSI.

[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
Similaire à `CDynamicStringAccessor` , à ceci près que cette classe demande des données accédées à partir de la banque de données en tant que données de chaîne UNICODE.

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
Un accesseur avec des méthodes pour gérer des colonnes et des paramètres de commande. Avec cette classe, vous pouvez utiliser des types de données tant que le fournisseur peut convertir le type.

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
Peut être utilisé comme argument de modèle lorsque vous ne souhaitez pas que la classe pour prendre en charge des paramètres ou des colonnes de sortie.

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
Similaire à `CDynamicStringAccessor` , sauf que cette classe convertit toutes les données accédées à partir du magasin de données au format XML (référencé).

## <a name="rowset-classes"></a>Classes de l’ensemble de lignes

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
Encapsule un ensemble de lignes et de ses accesseurs associés.

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
Utilisé pour accéder aux éléments d’un ensemble de lignes à l’aide de la syntaxe de tableau.

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
Utilisé pour extraire et manipuler les lignes en bloc en récupérant plusieurs handles de ligne avec un seul appel.

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
Peut être utilisé comme argument de modèle si la commande ne renvoie pas un ensemble de lignes.

[CRestrictions](../../data/oledb/crestrictions-class.md)<br/>
Permet de spécifier des restrictions pour les ensembles de lignes de schéma.

[CRowset](../../data/oledb/crowset-class.md)<br/>
Utilisé pour manipuler, définir et récupérer des données de l’ensemble de lignes.

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
Retourne un `ISequentialStream` l’objet au lieu d’un ensemble de lignes ; vous utilisez ensuite le `Read` méthode pour récupérer des données au format XML. (Notez que cette fonctionnalité fonctionne uniquement avec SQL Server 2000, SQL Server 2000 effectue la mise en forme.)

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
Fournit une implémentation factice pour `IRowsetNotify`, avec des fonctions vides pour le `IRowsetNotify` méthodes `OnFieldChange`, `OnRowChange`, et `OnRowsetChange`.

[Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

Les modèles OLE DB vous fournir un ensemble de classes qui correspondent aux ensembles de lignes de schéma OLE DB.

## <a name="command-classes"></a>Classes de commande

[CCommand](../../data/oledb/ccommand-class.md)<br/>
Utilisé pour définir et exécuter une commande OLE DB basée sur le paramètre. Pour simplement ouvrir un simple ensemble de lignes, utilisez `CTable` à la place.

[CMultipleResults](../../data/oledb/cmultipleresults-class.md)<br/>
Utilisé comme argument template pour la `CCommand` modèle lorsque vous souhaitez que la commande pour gérer plusieurs jeux de résultats.

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
Utilisé comme argument de modèle pour les classes de modèle, tel que `CCommand` et `CTable`, qui prennent un argument de classe d’accesseur. Utilisez `CNoAccessor` si vous ne souhaitez pas que la classe pour prendre en charge des paramètres ou des colonnes de sortie.

[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
Utilisé comme argument template pour la `CCommand` modèle lorsque vous souhaitez que la commande pour gérer un ensemble de lignes unique. `CNoMultipleResults` est la valeur par défaut pour l’argument de modèle.

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
Utilisé comme argument template pour `CCommand` ou `CTable` si la commande ou la table ne renvoie pas un ensemble de lignes.

[CTable](../../data/oledb/ctable-class.md)<br/>
Utilisé pour accéder à un ensemble de lignes simple sans paramètres.

## <a name="property-classes"></a>Classes de propriété

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
Utilisé pour passer un tableau d’ID de propriété pour lequel le consommateur souhaite les informations de propriété. Les propriétés appartiennent au jeu d’une propriété.

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
Utilisé pour définir des propriétés sur un fournisseur.

## <a name="bookmark-class"></a>Classe de signet

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
Utilisé en tant qu’index pour accéder aux données dans un ensemble de lignes.

## <a name="error-class"></a>Error (classe)

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
Permet de récupérer les informations d’erreur OLE DB.

## <a name="see-also"></a>Voir aussi

[Référence des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Modèles OLE DB](../../data/oledb/ole-db-templates.md)