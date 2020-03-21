---
title: CCustomSession (CustomSess.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
ms.openlocfilehash: 4775f21c1e0fa7666d24b4d6a55e099bc6ae55a2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079756"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*Personnalisé* Sess. H contient la déclaration et l’implémentation de l’objet de session OLE DB. L’objet de source de données crée l’objet de session et représente une conversation entre un consommateur et un fournisseur. Plusieurs sessions simultanées peuvent être ouvertes pour une source de données. La liste d’héritage pour `CCustomSession` suit :

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSession
class ATL_NO_VTABLE CCustomSession :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IGetDataSourceImpl<CCustomSession>,
   public IOpenRowsetImpl<CCustomSession>,
   public ISessionPropertiesImpl<CCustomSession>,
   public IObjectWithSiteSessionImpl<CCustomSession>,
   public IDBSchemaRowsetImpl<CCustomSession>,
   public IDBCreateCommandImpl<CCustomSession, CCustomCommand>
```

L’objet de session hérite de `IGetDataSource`, `IOpenRowset`, `ISessionProperties`et `IDBCreateCommand`. L’interface `IGetDataSource` permet à une session de récupérer la source de données qui l’a créée. Cela est utile si vous devez obtenir des propriétés à partir de la source de données que vous avez créée ou d’autres informations que la source de données peut fournir. L’interface `ISessionProperties` gère toutes les propriétés de la session. Les interfaces `IOpenRowset` et `IDBCreateCommand` sont utilisées pour le travail de base de données. Si le fournisseur prend en charge les commandes, il implémente l’interface `IDBCreateCommand`. Il est utilisé pour créer l’objet de commande qui peut exécuter des commandes. Le fournisseur implémente toujours l’objet `IOpenRowset`. Elle est utilisée pour générer un ensemble de lignes à partir d’un fournisseur. Il s’agit d’un ensemble de lignes par défaut (par exemple, `"select * from mytable"`) d’un fournisseur.

L’Assistant génère également trois classes de session : `CCustomSessionColSchema`, `CCustomSessionPTSchema`et `CCustomSessionTRSchema`. Ces sessions sont utilisées pour les ensembles de lignes de schéma. Les ensembles de lignes de schéma permettent au fournisseur de retourner des métadonnées au consommateur sans que le consommateur n’ait à exécuter une requête ou à extraire des données. L’extraction des métadonnées peut être beaucoup plus rapide que la recherche des fonctionnalités d’un fournisseur.

La spécification OLE DB exige que les fournisseurs qui implémentent l’interface `IDBSchemaRowset` prennent en charge trois types d’ensembles de lignes de schéma : DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES et DBSCHEMA_TABLES. L’Assistant génère des implémentations pour chaque ensemble de lignes de schéma. Chaque classe générée par l’Assistant contient une méthode `Execute`. Dans cette `Execute` méthode, vous pouvez retourner des données au fournisseur sur les tables, les colonnes et les types de données que vous prenez en charge. Ces données sont connues au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)<br/>
