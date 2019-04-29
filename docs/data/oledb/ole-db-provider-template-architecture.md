---
title: Architecture des modèles du fournisseur OLE DB
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: 65a7e5b8f169d06ca11d8d27ec99ce3db4b63014
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62283987"
---
# <a name="ole-db-provider-template-architecture"></a>Architecture des modèles du fournisseur OLE DB

## <a name="data-sources-and-sessions"></a>Sources de données et sessions

L’architecture du fournisseur OLE DB inclut un objet de source de données et une ou plusieurs sessions. L’objet de source de données est l’objet initial que chaque fournisseur doit instancier. Quand une application consommateur a besoin de données, il crée l’objet de source de données pour démarrer le fournisseur. L’objet de source de données crée un objet session (à l’aide de la `IDBCreateSession` interface) via lequel le consommateur se connecte à l’objet de source de données. Les programmeurs ODBC peuvent considérer que l’objet de source de données comme étant équivalent à la `HENV` et l’objet de session comme étant équivalents à le `HDBC`.

![Architecture du fournisseur](../../data/oledb/media/vc4twb1.gif "architecture du fournisseur")

Avec les fichiers sources créés par le **Assistant fournisseur OLE DB**, les modèles OLE DB implémentent un objet de source de données. Une session est un objet qui correspond à la norme OLE DB `TSession`.

## <a name="mandatory-and-optional-interfaces"></a>Interfaces obligatoires et facultatives

Les modèles du fournisseur OLE DB offrent des implémentations préconfigurées pour toutes les interfaces requises. Interfaces obligatoires et facultatives sont définies par OLE DB pour plusieurs types d’objets :

- [Source de données](../../data/oledb/data-source-object-interfaces.md)

- [Session](../../data/oledb/session-object-interfaces.md)

- [Rowset](../../data/oledb/rowset-object-interfaces.md)

- [Commande](../../data/oledb/command-object-interfaces.md)

- [Transaction](../../data/oledb/transaction-object-interfaces.md)

Les modèles du fournisseur OLE DB n’implémentent pas les objets de ligne et de stockage.

Le tableau suivant répertorie les interfaces obligatoires et facultatives pour les objets répertoriés ci-dessus, en fonction de la [OLE DB 2.6 SDK documentation sur](/previous-versions/windows/desktop/ms722784(v=vs.85)).

|Composant|Interface|Commentaire|
|---------------|---------------|-------------|
|[Source de données](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md))|[mandatory] `IDBCreateSession`<br /><br /> [mandatory] `IDBInitialize`<br /><br /> [mandatory] `IDBProperties`<br /><br /> [mandatory] `IPersist`<br /><br /> [optional] `IConnectionPointContainer`<br /><br /> [optional] `IDBAsynchStatus`<br /><br /> [optional] `IDBDataSourceAdmin`<br /><br /> [optional] `IDBInfo`<br /><br /> [optional] `IPersistFile`<br /><br /> [optional] `ISupportErrorInfo`|Connexion du consommateur au fournisseur. L’objet est utilisé pour spécifier des propriétés sur la connexion comme nom de source de données ID et mot de passe utilisateur. L’objet peut également être utilisé pour administrer une source de données (créer, mettre à jour, supprimer, des tables et ainsi de suite).|
|[Session](../../data/oledb/session-object-interfaces.md) ([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[mandatory] `IGetDataSource`<br /><br /> [mandatory] `IOpenRowset`<br /><br /> [mandatory] `ISessionProperties`<br /><br /> [optional] `IAlterIndex`<br /><br /> [optional] `IAlterTable`<br /><br /> [optional] `IBindResource`<br /><br /> [optional] `ICreateRow`<br /><br /> [optional] `IDBCreateCommand`<br /><br /> [optional] `IDBSchemaRowset`<br /><br /> [optional] `IIndexDefinition`<br /><br /> [optional] `ISupportErrorInfo`<br /><br /> [optional] `ITableCreation`<br /><br /> [optional] `ITableDefinition`<br /><br /> [optional] `ITableDefinitionWithConstraints`<br /><br /> [optional] `ITransaction`<br /><br /> [optional] `ITransactionJoin`<br /><br /> [optional] `ITransactionLocal`<br /><br /> [optional] `ITransactionObject`|L’objet de session est une même conversation entre un consommateur et le fournisseur. Elle est similaire à ODBC `HSTMT` dans la mesure où il peut y avoir plusieurs sessions simultanées active.<br /><br /> L’objet session est le lien principal pour accéder à la fonctionnalité OLE DB. Pour accéder à une commande, une transaction ou un objet d’ensemble de lignes, vous accédez via l’objet de session.|
|[Ensemble de lignes](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] `IConvertType`<br /><br /> [mandatory] `IRowset`<br /><br /> [mandatory] `IRowsetInfo`<br /><br /> [optional] `IChapteredRowset`<br /><br /> [optional] `IColumnsInfo2`<br /><br /> [optional] `IColumnsRowset`<br /><br /> [optional] `IConnectionPointContainer`<br /><br /> [optional] `IDBAsynchStatus`<br /><br /> [optional] `IGetRow`<br /><br /> [optional] `IRowsetChange`<br /><br /> [optional] `IRowsetChapterMember`<br /><br /> [optional] `IRowsetCurrentIndex`<br /><br /> [optional] `IRowsetFind`<br /><br /> [optional] `IRowsetIdentity`<br /><br /> [optional] `IRowsetIndex`<br /><br /> [optional] `IRowsetLocate`<br /><br /> [optional] `IRowsetRefresh`<br /><br /> [optional] `IRowsetScroll`<br /><br /> [optional] `IRowsetUpdate`<br /><br /> [optional] `IRowsetView`<br /><br /> [optional] `ISupportErrorInfo`<br /><br /> [optional] `IRowsetBookmark`|L’objet d’ensemble de lignes est les données à partir de la source de données. L’objet est utilisé pour les liaisons de données et les opérations de base (mise à jour, extraction, de déplacement et d’autres) sur les données. Vous avez toujours un objet d’ensemble de lignes à conserver et de manipuler des données.|
|[Command](../../data/oledb/command-object-interfaces.md) ([CCommand](ccommand-class.md))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] `ICommand`<br /><br /> [mandatory] `ICommandProperties`<br /><br /> [mandatory] `ICommandText`<br /><br /> [mandatory] `IConvertType`<br /><br /> [optional] `IColumnsRowset`<br /><br /> [optional] `ICommandPersist`<br /><br /> [optional] `ICommandPrepare`<br /><br /> [optional] `ICommandWithParameters`<br /><br /> [optional] `ISupportErrorInfo`<br /><br /> [optional] `ICommandStream`|L’objet de commande gère les opérations de données telles que les requêtes. Il peut gérer des instructions paramétrées ou non paramétrées.<br /><br /> L’objet de commande est également responsable du traitement des liaisons pour les paramètres et les colonnes de sortie. Une liaison est une structure qui contient des informations sur la façon dont une colonne, dans un ensemble de lignes doit être récupérée. Il contient des informations telles que l’ordinal, type de données, longueur et état.|
|[Transaction](../../data/oledb/transaction-object-interfaces.md) (facultatif)|[mandatory] `IConnectionPointContainer`<br /><br /> [mandatory] `ITransaction`<br /><br /> [optional] `ISupportErrorInfo`|L’objet de transaction définit une unité atomique de travail sur une source de données et détermine la façon dont ces unités de travail sont liés entre eux. Cet objet n’est pas directement pris en charge par les modèles du fournisseur OLE DB (autrement dit, vous créez votre propre objet).|

Pour plus d’informations, consultez les rubriques suivantes :

- [Mappages des propriétés](../../data/oledb/property-maps.md)

- [L’enregistrement de l’utilisateur](../../data/oledb/user-record.md)

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Interfaces OLE DB](/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
