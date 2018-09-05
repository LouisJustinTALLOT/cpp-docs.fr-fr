---
title: Architecture des modèles de fournisseur OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ebebb7f69239b62cf276e955fd6e54ef0cf37ea4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684288"
---
# <a name="ole-db-provider-template-architecture"></a>Architecture des modèles du fournisseur OLE DB
## <a name="data-sources-and-sessions"></a>Sources de données et sessions  
 L’architecture du fournisseur OLE DB inclut un objet de source de données et une ou plusieurs sessions. L’objet de source de données est l’objet initial que chaque fournisseur doit instancier. Quand une application consommateur a besoin de données, il crée l’objet de source de données pour démarrer le fournisseur. L’objet de source de données crée un objet session (à l’aide de la `IDBCreateSession` interface) via lequel le consommateur se connecte à l’objet de source de données. Les programmeurs ODBC peuvent considérer que l’objet de source de données comme étant équivalent à la `HENV` et l’objet de session comme étant équivalents à le `HDBC`.  
  
 ![Architecture du fournisseur](../../data/oledb/media/vc4twb1.gif "vc4twb1")  
  
 Avec les fichiers sources créés par l’Assistant fournisseur OLE DB, les modèles OLE DB implémentent un objet de source de données. Une session est un objet qui correspond à la norme OLE DB `TSession`.  
  
## <a name="mandatory-and-optional-interfaces"></a>Interfaces obligatoires et facultatives  
 Les modèles du fournisseur OLE DB offrent des implémentations préconfigurées pour toutes les interfaces requises. Interfaces obligatoires et facultatives sont définies par OLE DB pour plusieurs types d’objets :  
  
-   [Source de données](../../data/oledb/data-source-object-interfaces.md)  
  
-   [Session](../../data/oledb/session-object-interfaces.md)  
  
-   [Rowset](../../data/oledb/rowset-object-interfaces.md)  
  
-   [Commande](../../data/oledb/command-object-interfaces.md)  
  
-   [Transaction](../../data/oledb/transaction-object-interfaces.md)  
  
 Notez que les modèles du fournisseur OLE DB n’implémentent pas les objets de ligne et de stockage.  
  
 Le tableau suivant répertorie les interfaces obligatoires et facultatives pour les objets répertoriés ci-dessus, en fonction de la [OLE DB 2.6 SDK documentation sur](/previous-versions/windows/desktop/ms722784\(v=vs.85\)).  
  
|Composant|Interface|Commentaire|  
|---------------|---------------|-------------|  
|[Source de données](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md))|[obligatoire] `IDBCreateSession`<br /><br /> [obligatoire] `IDBInitialize`<br /><br /> [obligatoire] `IDBProperties`<br /><br /> [obligatoire] `IPersist`<br /><br /> [facultatif] `IConnectionPointContainer`<br /><br /> [facultatif] `IDBAsynchStatus`<br /><br /> [facultatif] `IDBDataSourceAdmin`<br /><br /> [facultatif] `IDBInfo`<br /><br /> [facultatif] `IPersistFile`<br /><br /> [facultatif] `ISupportErrorInfo`|Connexion du consommateur au fournisseur. L’objet est utilisé pour spécifier des propriétés sur la connexion comme nom de source de données ID et mot de passe utilisateur. L’objet peut également être utilisé pour administrer une source de données (créer, mettre à jour, supprimer, des tables et ainsi de suite).|  
|[Session](../../data/oledb/session-object-interfaces.md) ([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[obligatoire] `IGetDataSource`<br /><br /> [obligatoire] `IOpenRowset`<br /><br /> [obligatoire] `ISessionProperties`<br /><br /> [facultatif] `IAlterIndex`<br /><br /> [facultatif] `IAlterTable`<br /><br /> [facultatif] `IBindResource`<br /><br /> [facultatif] `ICreateRow`<br /><br /> [facultatif] `IDBCreateCommand`<br /><br /> [facultatif] `IDBSchemaRowset`<br /><br /> [facultatif] `IIndexDefinition`<br /><br /> [facultatif] `ISupportErrorInfo`<br /><br /> [facultatif] `ITableCreation`<br /><br /> [facultatif] `ITableDefinition`<br /><br /> [facultatif] `ITableDefinitionWithConstraints`<br /><br /> [facultatif] `ITransaction`<br /><br /> [facultatif] `ITransactionJoin`<br /><br /> [facultatif] `ITransactionLocal`<br /><br /> [facultatif] `ITransactionObject`|L’objet de session représente une même conversation entre un consommateur et le fournisseur. Il est quelque peu similaire à ODBC `HSTMT` dans la mesure où il peut y avoir plusieurs sessions simultanées active.<br /><br /> L’objet session est le lien principal pour accéder à la fonctionnalité OLE DB. Pour accéder à une commande, une transaction ou un objet d’ensemble de lignes, vous accédez via l’objet de session.|  
|[Ensemble de lignes](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|[obligatoire] `IAccessor`<br /><br /> [obligatoire] `IColumnsInfo`<br /><br /> [obligatoire] `IConvertType`<br /><br /> [obligatoire] `IRowset`<br /><br /> [obligatoire] `IRowsetInfo`<br /><br /> [facultatif] `IChapteredRowset`<br /><br /> [facultatif] `IColumnsInfo2`<br /><br /> [facultatif] `IColumnsRowset`<br /><br /> [facultatif] `IConnectionPointContainer`<br /><br /> [facultatif] `IDBAsynchStatus`<br /><br /> [facultatif] `IGetRow`<br /><br /> [facultatif] `IRowsetChange`<br /><br /> [facultatif] `IRowsetChapterMember`<br /><br /> [facultatif] `IRowsetCurrentIndex`<br /><br /> [facultatif] `IRowsetFind`<br /><br /> [facultatif] `IRowsetIdentity`<br /><br /> [facultatif] `IRowsetIndex`<br /><br /> [facultatif] `IRowsetLocate`<br /><br /> [facultatif] `IRowsetRefresh`<br /><br /> [facultatif] `IRowsetScroll`<br /><br /> [facultatif] `IRowsetUpdate`<br /><br /> [facultatif] `IRowsetView`<br /><br /> [facultatif] `ISupportErrorInfo`<br /><br /> [facultatif] `IRowsetBookmark`|L’objet rowset représente les données à partir de la source de données. L’objet est chargé pour les liaisons de données et les opérations de base (mise à jour, extraction, de déplacement et d’autres) sur les données. Vous avez toujours un objet rowset pour contenir et manipuler des données.|  
|[Commande](../../data/oledb/command-object-interfaces.md) ([CCommand](ccommand-class.md))|[obligatoire] `IAccessor`<br /><br /> [obligatoire] `IColumnsInfo`<br /><br /> [obligatoire] `ICommand`<br /><br /> [obligatoire] `ICommandProperties`<br /><br /> [obligatoire] `ICommandText`<br /><br /> [obligatoire] `IConvertType`<br /><br /> [facultatif] `IColumnsRowset`<br /><br /> [facultatif] `ICommandPersist`<br /><br /> [facultatif] `ICommandPrepare`<br /><br /> [facultatif] `ICommandWithParameters`<br /><br /> [facultatif] `ISupportErrorInfo`<br /><br /> [facultatif] `ICommandStream`|L’objet de commande gère les opérations de données telles que les requêtes. Il peut gérer des instructions paramétrées ou non paramétrées.<br /><br /> L’objet de commande est également responsable du traitement des liaisons pour les paramètres et les colonnes de sortie. Une liaison est une structure qui contient des informations sur la façon dont une colonne, dans un ensemble de lignes doit être récupérée. Il contient des informations telles que l’ordinal, type de données, longueur et état.|  
|[Transaction](../../data/oledb/transaction-object-interfaces.md) (facultatif)|[obligatoire] `IConnectionPointContainer`<br /><br /> [obligatoire] `ITransaction`<br /><br /> [facultatif] `ISupportErrorInfo`|L’objet de transaction définit une unité atomique de travail sur une source de données et détermine la façon dont ces unités de travail sont liés entre eux. Cet objet n’est pas directement pris en charge par les modèles du fournisseur OLE DB (autrement dit, vous créez votre propre objet).|  
  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Mappages des propriétés](../../data/oledb/property-maps.md)  
  
-   [L’enregistrement de l’utilisateur](../../data/oledb/user-record.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Interfaces OLE DB](/previous-versions/windows/desktop/ms709709\(v=vs.85\))