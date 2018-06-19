---
title: Référence des modèles de consommateur OLE DB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5b599a1c7a1b256cc9c56d772a15621beda286f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112054"
---
# <a name="ole-db-consumer-templates-reference"></a>Référence des modèles du consommateur OLE DB
Modèles du consommateur OLE DB contient les classes suivantes. La documentation de référence inclut également des rubriques sur la [macros pour les modèles du consommateur OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="session-classes"></a>Classes de session  
 [CDataConnection](../../data/oledb/cdataconnection-class.md)  
 Gère la connexion avec la source de données. Cette classe est utile pour la création de clients, car elle encapsule les objets nécessaires (source de données et session) et la partie du travail, que vous devez effectuer lors de la connexion à une source de données.  
  
 [CDataSource](../../data/oledb/cdatasource-class.md)  
 Correspond à un objet de source de données OLE DB, qui représente une connexion via un fournisseur de source de données. Un ou plusieurs sessions base de données, chacun représenté par un `CSession` d’objet, peuvent avoir lieu sur une connexion unique.  
  
 [CEnumerator](../../data/oledb/cenumerator-class.md)  
 Correspond à un objet énumérateur OLE DB, qui Récupère l’ensemble de lignes d’informations sur les sources de données disponibles.  
  
 [CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)  
 Utilisé par `CEnumerator` pour accéder aux données à partir de l’ensemble de lignes d’énumérateur. Cet ensemble de lignes se compose des sources de données et les énumérateurs visibles à partir de l’énumérateur en cours.  
  
 [CSession](../../data/oledb/csession-class.md)  
 Représente une session d’accès de base de données unique. Une ou plusieurs sessions peuvent être associée à chaque `CDataSource` objet.  
  
## <a name="accessor-classes"></a>Classes d’accesseurs  
 [CAccessor](../../data/oledb/caccessor-class.md)  
 Utilisé pour les enregistrements qui sont liées statiquement à une source de données. Utilisez cette classe d’accesseur lorsque vous connaissez la structure de la source de données.  
  
 [CAccessorBase](../../data/oledb/caccessorbase-class.md)  
 Classe de base pour toutes les classes d’accesseur.  
  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)  
 Un accesseur qui peut être créé au moment de l’exécution, selon les informations de colonne de l’ensemble de lignes. Cette classe permet de récupérer les données si vous ne connaissez pas la structure de la source de données.  
  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)  
 Un accesseur qui peut être utilisé lorsque les types de commande sont inconnus. Obtient les informations de paramètre en appelant le `ICommandWithParameters` de l’interface, si le fournisseur prend en charge l’interface.  
  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)  
 Permet d’accéder à une source de données lorsque vous n’avez aucune connaissance de la structure sous-jacente de la base de données.  
  
 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)  
 Semblable à `CDynamicStringAccessor` , sauf que cette classe demande des données accédées à partir de la banque de données en tant que données de chaîne ANSI.  
  
 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)  
 Semblable à `CDynamicStringAccessor` , sauf que cette classe demande des données accédées à partir de la banque de données en tant que données de chaîne UNICODE.  
  
 [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)  
 Un accesseur avec des méthodes pour gérer les colonnes et les paramètres de commande. Avec cette classe, vous pouvez utiliser des types de données tant que le fournisseur peut convertir le type.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Peut être utilisé comme argument de modèle lorsque vous ne souhaitez pas la classe pour prendre en charge des paramètres ou des colonnes de sortie.  
  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)  
 Semblable à `CDynamicStringAccessor` , sauf que cette classe convertit toutes les données accédées à partir du magasin de données au format XML (avec balises).  
  
## <a name="rowset-classes"></a>Classes de l’ensemble de lignes  
 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)  
 Encapsule un ensemble de lignes et de ses accesseurs associés.  
  
 [CArrayRowset](../../data/oledb/carrayrowset-class.md)  
 Utilisé pour accéder aux éléments d’un ensemble de lignes à l’aide de la syntaxe de tableau.  
  
 [CBulkRowset](../../data/oledb/cbulkrowset-class.md)  
 Utilisé pour extraire et manipuler les lignes en bloc en récupérant plusieurs handles de ligne avec un seul appel.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Peut être utilisé comme argument de modèle si la commande ne renvoie pas un ensemble de lignes.  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md)  
 Permet de spécifier des restrictions pour les ensembles de lignes de schéma.  
  
 [CRowset](../../data/oledb/crowset-class.md)  
 Utilisé pour manipuler, définir et récupérer des données de l’ensemble de lignes.  
  
 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)  
 Retourne un `ISequentialStream` l’objet au lieu d’un ensemble de lignes ; vous utilisez ensuite le **en lecture** méthode pour récupérer des données au format XML. (Notez que cette fonctionnalité fonctionne uniquement avec SQL Server 2000, SQL Server 2000 effectue la mise en forme.)  
  
 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)  
 Fournit une implémentation factice pour `IRowsetNotify`, avec des fonctions vides pour le `IRowsetNotify` méthodes `OnFieldChange`, `OnRowChange`, et `OnRowsetChange`.  
  
 [Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
 Les modèles OLE DB vous fournir un ensemble de classes qui correspondent aux ensembles de lignes de schéma OLE DB.  
  
## <a name="command-classes"></a>Classes de commande  
 [CCommand](../../data/oledb/ccommand-class.md)  
 Utilisé pour définir et exécuter une commande OLE DB basée sur le paramètre. Pour simplement ouvrir un ensemble de lignes simple, utilisez `CTable` à la place.  
  
 [CMultipleResults](../../data/oledb/cmultipleresults-class.md)  
 Utilisé comme argument de modèle pour la `CCommand` modèle lorsque vous souhaitez que la commande pour gérer plusieurs jeux de résultats.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Utilisé comme argument de modèle pour les classes de modèle, telles que `CCommand` et `CTable`, qui prennent un argument de classe d’accesseur. Utilisez `CNoAccessor` si vous ne souhaitez pas la classe pour prendre en charge des paramètres ou des colonnes de sortie.  
  
 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)  
 Utilisé comme argument de modèle pour la `CCommand` modèle lorsque vous souhaitez que la commande pour gérer un ensemble de lignes unique. `CNoMultipleResults` est la valeur par défaut pour l’argument de modèle.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Utilisé comme argument template pour `CCommand` ou `CTable` si la commande ou table ne renvoie pas un ensemble de lignes.  
  
 [CTable](../../data/oledb/ctable-class.md)  
 Utilisé pour accéder à un ensemble de lignes simple sans paramètres.  
  
## <a name="property-classes"></a>Classes de propriété  
 [CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)  
 Utilisé pour passer un tableau d’ID de propriété pour lequel le consommateur souhaite obtenir des informations sur les propriétés. Les propriétés appartiennent au jeu d’une propriété.  
  
 [CDBPropSet](../../data/oledb/cdbpropset-class.md)  
 Permet de définir des propriétés sur un fournisseur.  
  
## <a name="bookmark-class"></a>Classe de signet  
 [CBookmark](../../data/oledb/cbookmark-class.md)  
 Utilisé en tant qu’index pour accéder aux données dans un ensemble de lignes.  
  
## <a name="error-class"></a>Error (classe)  
 [CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)  
 Utilisé pour récupérer les informations d’erreur OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des modèles de fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)   
 [Modèles OLE DB](../../data/oledb/ole-db-templates.md)