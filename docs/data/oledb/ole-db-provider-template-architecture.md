---
description: 'En savoir plus sur : architecture de modèle de fournisseur OLE DB'
title: Architecture des modèles du fournisseur OLE DB
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: 1cc1619ab7ed13c2d7962f75229df2ecd8cf0d78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317127"
---
# <a name="ole-db-provider-template-architecture"></a>Architecture des modèles du fournisseur OLE DB

## <a name="data-sources-and-sessions"></a>Sources de données et sessions

L’architecture du fournisseur OLE DB comprend un objet source de données et une ou plusieurs sessions. L’objet source de données est l’objet initial que chaque fournisseur doit instancier. Lorsqu’une application cliente a besoin de données, elle crée l’objet de source de données pour démarrer le fournisseur. L’objet de source de données crée un objet de session (à l’aide de l' `IDBCreateSession` interface) par le biais duquel le consommateur se connecte à l’objet source de données. Les programmeurs ODBC peuvent considérer que l’objet de source de données équivaut à `HENV` et à l’objet de session comme équivalent à `HDBC` .

![Architecture de fournisseur](../../data/oledb/media/vc4twb1.gif "Architecture de fournisseur")

Avec les fichiers sources créés par l' **assistant OLE DB fournisseur**, les modèles de OLE DB implémentent un objet de source de données. Une session est un objet qui correspond à l’OLE DB `TSession` .

## <a name="mandatory-and-optional-interfaces"></a>Interfaces obligatoires et facultatives

Les modèles du fournisseur OLE DB fournissent des implémentations préemballées pour toutes les interfaces requises. Les interfaces obligatoires et facultatives sont définies par OLE DB pour plusieurs types d’objets :

- [Source de données](../../data/oledb/data-source-object-interfaces.md)

- [Session](../../data/oledb/session-object-interfaces.md)

- [Ensemble de lignes](../../data/oledb/rowset-object-interfaces.md)

- [Commande](../../data/oledb/command-object-interfaces.md)

- [Transaction](../../data/oledb/transaction-object-interfaces.md)

Les modèles de fournisseur OLE DB n’implémentent pas les objets Row et Storage.

Le tableau suivant répertorie les interfaces obligatoires et facultatives pour les objets répertoriés ci-dessus, conformément à la [documentation du kit de développement logiciel (SDK) OLE DB 2,6](/previous-versions/windows/desktop/ms722784(v=vs.85)).

|Composant|Interface|Commentaire|
|---------------|---------------|-------------|
|[Source de données](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md))|requise `IDBCreateSession`<br /><br /> requise `IDBInitialize`<br /><br /> requise `IDBProperties`<br /><br /> requise `IPersist`<br /><br /> facultatif `IConnectionPointContainer`<br /><br /> facultatif `IDBAsynchStatus`<br /><br /> facultatif `IDBDataSourceAdmin`<br /><br /> facultatif `IDBInfo`<br /><br /> facultatif `IPersistFile`<br /><br /> facultatif `ISupportErrorInfo`|Connexion du consommateur au fournisseur. L’objet est utilisé pour spécifier des propriétés sur la connexion, telles que l’ID utilisateur, le mot de passe et le nom de la source de données. L’objet peut également être utilisé pour administrer une source de données (créer, mettre à jour, supprimer, tables, etc.).|
|[Session](../../data/oledb/session-object-interfaces.md) ([CSession](./cdataconnection-class.md#op_csession_amp))|requise `IGetDataSource`<br /><br /> requise `IOpenRowset`<br /><br /> requise `ISessionProperties`<br /><br /> facultatif `IAlterIndex`<br /><br /> facultatif `IAlterTable`<br /><br /> facultatif `IBindResource`<br /><br /> facultatif `ICreateRow`<br /><br /> facultatif `IDBCreateCommand`<br /><br /> facultatif `IDBSchemaRowset`<br /><br /> facultatif `IIndexDefinition`<br /><br /> facultatif `ISupportErrorInfo`<br /><br /> facultatif `ITableCreation`<br /><br /> facultatif `ITableDefinition`<br /><br /> facultatif `ITableDefinitionWithConstraints`<br /><br /> facultatif `ITransaction`<br /><br /> facultatif `ITransactionJoin`<br /><br /> facultatif `ITransactionLocal`<br /><br /> facultatif `ITransactionObject`|L’objet session est une conversation unique entre un consommateur et un fournisseur. Elle est similaire à l’ODBC `HSTMT` dans la mesure où il peut y avoir plusieurs sessions simultanées actives.<br /><br /> L’objet session est le lien principal permettant d’accéder à OLE DB fonctionnalité. Pour accéder à une commande, une transaction ou un objet Rowset, vous parcourez l’objet session.|
|[Ensemble de lignes](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|requise `IAccessor`<br /><br /> requise `IColumnsInfo`<br /><br /> requise `IConvertType`<br /><br /> requise `IRowset`<br /><br /> requise `IRowsetInfo`<br /><br /> facultatif `IChapteredRowset`<br /><br /> facultatif `IColumnsInfo2`<br /><br /> facultatif `IColumnsRowset`<br /><br /> facultatif `IConnectionPointContainer`<br /><br /> facultatif `IDBAsynchStatus`<br /><br /> facultatif `IGetRow`<br /><br /> facultatif `IRowsetChange`<br /><br /> facultatif `IRowsetChapterMember`<br /><br /> facultatif `IRowsetCurrentIndex`<br /><br /> facultatif `IRowsetFind`<br /><br /> facultatif `IRowsetIdentity`<br /><br /> facultatif `IRowsetIndex`<br /><br /> facultatif `IRowsetLocate`<br /><br /> facultatif `IRowsetRefresh`<br /><br /> facultatif `IRowsetScroll`<br /><br /> facultatif `IRowsetUpdate`<br /><br /> facultatif `IRowsetView`<br /><br /> facultatif `ISupportErrorInfo`<br /><br /> facultatif `IRowsetBookmark`|L’objet d’ensemble de lignes est les données de la source de données. L’objet est utilisé pour les liaisons de ces données et toutes les opérations de base (mise à jour, extraction, déplacement et autres) sur les données. Vous disposez toujours d’un objet d’ensemble de lignes pour conserver et manipuler les données.|
|[Commande](../../data/oledb/command-object-interfaces.md) ([CCommand](ccommand-class.md))|requise `IAccessor`<br /><br /> requise `IColumnsInfo`<br /><br /> requise `ICommand`<br /><br /> requise `ICommandProperties`<br /><br /> requise `ICommandText`<br /><br /> requise `IConvertType`<br /><br /> facultatif `IColumnsRowset`<br /><br /> facultatif `ICommandPersist`<br /><br /> facultatif `ICommandPrepare`<br /><br /> facultatif `ICommandWithParameters`<br /><br /> facultatif `ISupportErrorInfo`<br /><br /> facultatif `ICommandStream`|L’objet Command gère les opérations sur les données telles que les requêtes. Il peut gérer des instructions paramétrables ou non paramétrées.<br /><br /> L’objet Command est également chargé de gérer les liaisons pour les paramètres et les colonnes de sortie. Une liaison est une structure qui contient des informations sur la façon dont une colonne d’un ensemble de lignes doit être récupérée. Elle contient des informations telles que l’ordinal, le type de données, la longueur et l’État.|
|[Transaction](../../data/oledb/transaction-object-interfaces.md) (facultatif)|requise `IConnectionPointContainer`<br /><br /> requise `ITransaction`<br /><br /> facultatif `ISupportErrorInfo`|L’objet transaction définit une unité de travail atomique sur une source de données et détermine la relation entre ces unités de travail. Cet objet n’est pas directement pris en charge par les modèles du fournisseur OLE DB (autrement dit, vous créez votre propre objet).|

Pour plus d'informations, voir les rubriques suivantes :

- [Mappages de propriétés](../../data/oledb/property-maps.md)

- [Enregistrement utilisateur](../../data/oledb/user-record.md)

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Interfaces OLE DB](/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
