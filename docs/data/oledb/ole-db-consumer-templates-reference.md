---
title: Référence des modèles du consommateur OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: 13805ab1dc2c2b4792fd05c9140006c610b42f75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210104"
---
# <a name="ole-db-consumer-templates-reference"></a>Référence des modèles du consommateur OLE DB

Les modèles de consommateur OLE DB contiennent les classes suivantes. La documentation de référence comprend également des rubriques sur les [macros pour les modèles de consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="session-classes"></a>Classes de session

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
Gère la connexion à la source de données. Il s’agit d’une classe utile pour la création de clients, car elle encapsule les objets nécessaires (source de données et session) et une partie du travail que vous devez effectuer lors de la connexion à une source de données.

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
Correspond à un objet de source de données OLE DB, représentant une connexion via un fournisseur à une source de données. Une ou plusieurs sessions de base de données, chacune représentée par un objet `CSession`, peuvent avoir lieu sur une seule connexion.

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
Correspond à un objet énumérateur OLE DB, qui récupère des informations d’ensemble de lignes sur les sources de données disponibles.

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
Utilisé par `CEnumerator` pour accéder aux données de l’ensemble de lignes de l’énumérateur. Cet ensemble de lignes se compose des sources de données et des énumérateurs visibles à partir de l’énumérateur actuel.

[CSession](../../data/oledb/csession-class.md)<br/>
Représente une session d’accès à la base de données unique. Une ou plusieurs sessions peuvent être associées à chaque objet `CDataSource`.

## <a name="accessor-classes"></a>Classes d’accesseur

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
Utilisé pour les enregistrements liés de manière statique à une source de données. Utilisez cette classe d’accesseur lorsque vous connaissez la structure de la source de données.

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
Classe de base pour toutes les classes d’accesseur.

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
Accesseur qui peut être créé au moment de l’exécution, en fonction des informations de colonne de l’ensemble de lignes. Utilisez cette classe pour récupérer des données si vous ne connaissez pas la structure de la source de données.

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
Accesseur qui peut être utilisé lorsque les types de commande sont inconnus. Obtient les informations sur les paramètres en appelant l’interface `ICommandWithParameters`, si le fournisseur prend en charge l’interface.

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
Vous permet d’accéder à une source de données lorsque vous n’avez aucune connaissance de la structure sous-jacente de la base de données.

[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
Semblable à `CDynamicStringAccessor`, sauf que cette classe demande des données accessibles depuis le magasin de données en tant que données de chaîne ANSI.

[CDynamicStringAccessorW,](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
Semblable à `CDynamicStringAccessor`, sauf que cette classe demande des données accessibles depuis le magasin de données en tant que données de chaîne UNICODE.

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
Accesseur avec des méthodes pour gérer les colonnes et les paramètres de commande. Avec cette classe, vous pouvez utiliser n’importe quel type de données, à condition que le fournisseur puisse convertir le type.

[Cnoaccessor,](../../data/oledb/cnoaccessor-class.md)<br/>
Peut être utilisé comme argument de modèle lorsque vous ne souhaitez pas que la classe prenne en charge des paramètres ou des colonnes de sortie.

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
Semblable à `CDynamicStringAccessor`, sauf que cette classe convertit toutes les données accessibles depuis le magasin de données en tant que données au format XML (balises).

## <a name="rowset-classes"></a>Classes d’ensemble de lignes

[CAccessorRowset,](../../data/oledb/caccessorrowset-class.md)<br/>
Encapsule un ensemble de lignes et ses accesseurs associés.

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
Utilisé pour accéder aux éléments d’un ensemble de lignes à l’aide de la syntaxe de tableau.

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
Permet d’extraire et de manipuler des lignes en bloc en extrayant plusieurs descripteurs de ligne avec un seul appel.

[Cnorowset,](../../data/oledb/cnorowset-class.md)<br/>
Peut être utilisé comme argument de modèle si la commande ne retourne pas d’ensemble de lignes.

[CRestrictions](../../data/oledb/crestrictions-class.md)<br/>
Utilisé pour spécifier des restrictions pour les ensembles de lignes de schéma.

[CRowset](../../data/oledb/crowset-class.md)<br/>
Utilisé pour manipuler, définir et récupérer des données d’ensemble de lignes.

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
Retourne un objet `ISequentialStream` plutôt qu’un ensemble de lignes ; vous utilisez ensuite la méthode `Read` pour récupérer des données au format XML. (SQL Server 2000 effectue la mise en forme. Notez que cette fonctionnalité fonctionne avec SQL Server 2000 uniquement.)

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
Fournit une implémentation factice pour `IRowsetNotify`, avec des fonctions vides pour les méthodes de `IRowsetNotify` `OnFieldChange`, `OnRowChange`et `OnRowsetChange`.

[Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

Les modèles OLE DB fournissent un ensemble de classes qui correspondent aux ensembles de lignes de schéma OLE DB.

## <a name="command-classes"></a>Classes de commande

[CCommand](../../data/oledb/ccommand-class.md)<br/>
Utilisé pour définir et exécuter une commande OLE DB basée sur des paramètres. Pour simplement ouvrir un ensemble de lignes simple, utilisez `CTable` à la place.

[CMultipleResults](../../data/oledb/cmultipleresults-class.md)<br/>
Utilisé comme argument template pour le modèle `CCommand` lorsque vous souhaitez que la commande gère plusieurs jeux de résultats.

[Cnoaccessor,](../../data/oledb/cnoaccessor-class.md)<br/>
Utilisé comme argument de modèle pour les classes de modèle, telles que `CCommand` et `CTable`, qui acceptent un argument de classe d’accesseur. Utilisez `CNoAccessor` si vous ne souhaitez pas que la classe prenne en charge les paramètres ou les colonnes de sortie.

[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
Utilisé comme argument template pour le modèle `CCommand` lorsque vous souhaitez que la commande gère un seul ensemble de lignes. `CNoMultipleResults` est la valeur par défaut de l’argument template.

[Cnorowset,](../../data/oledb/cnorowset-class.md)<br/>
Utilisé comme argument template pour `CCommand` ou `CTable` si la commande ou la table ne retourne pas d’ensemble de lignes.

[CTable](../../data/oledb/ctable-class.md)<br/>
Utilisé pour accéder à un ensemble de lignes simple sans paramètres.

## <a name="property-classes"></a>Classes de propriété

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
Utilisé pour passer un tableau d’ID de propriété dont le consommateur souhaite obtenir des informations de propriété. Les propriétés appartiennent à un jeu de propriétés.

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
Utilisé pour définir les propriétés d’un fournisseur.

## <a name="bookmark-class"></a>Bookmark (classe)

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
Utilisé comme index pour accéder aux données d’un ensemble de lignes.

## <a name="error-class"></a>Error (classe)

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
Utilisé pour récupérer les informations d’erreur de OLE DB.

## <a name="see-also"></a>Voir aussi

[Référence des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Modèles OLE DB](../../data/oledb/ole-db-templates.md)
