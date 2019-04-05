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
ms.openlocfilehash: 5cb462aba671e79450e9ee7b8447410252f8edc9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023462"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*Custom*Sess.H contient la déclaration et l’implémentation de l’objet de session OLE DB. L’objet de source de données crée l’objet de session et représente une conversation entre un consommateur et un fournisseur. Plusieurs sessions simultanées peuvent être ouverts pour une source de données. La liste d’héritage pour `CCustomSession` suit :

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

Hérite de l’objet de session `IGetDataSource`, `IOpenRowset`, `ISessionProperties`, et `IDBCreateCommand`. Le `IGetDataSource` interface permet à une session récupérer la source de données qui l’a créée. Cela est utile si vous avez besoin obtenir des propriétés de la source de données que vous avez créé ou d’autres informations que la source de données peut fournir. Le `ISessionProperties` interface gère toutes les propriétés de la session. Le `IOpenRowset` et `IDBCreateCommand` interfaces sont utilisées pour effectuer le travail de base de données. Si le fournisseur prend en charge les commandes, il implémente le `IDBCreateCommand` interface. Il est utilisé pour créer l’objet de commande qui peut exécuter des commandes. Le fournisseur implémente toujours les `IOpenRowset` objet. Il est utilisé pour générer un ensemble de lignes à partir d’un fournisseur. Il est un ensemble de lignes par défaut (par exemple, `"select * from mytable"`) à partir d’un fournisseur.

L’Assistant génère également trois classes de session : `CCustomSessionColSchema`, `CCustomSessionPTSchema`, et `CCustomSessionTRSchema`. Ces sessions sont utilisées pour les ensembles de lignes de schéma. Ensembles de lignes de schéma permettent au fournisseur retourner des métadonnées au consommateur sans que celui-ci ait à exécuter une requête ou l’extraction des données. L’extraction de métadonnées peut être beaucoup plus rapide que la recherche les fonctionnalités d’un fournisseur.

La spécification OLE DB requiert que fournisseurs qui implémentent le `IDBSchemaRowset` types d’ensemble de lignes du schéma interface prise en charge trois : DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES et DBSCHEMA_TABLES. L’Assistant génère des implémentations pour chaque ensemble de lignes de schéma. Chaque classe générée par l’Assistant contient un `Execute` (méthode). Dans ce `Execute` (méthode), vous pouvez retourner des données pour le fournisseur sur les tables, les colonnes et les types de données que vous prenez en charge. Ces données sont connues au moment de la compilation.

## <a name="see-also"></a>Voir aussi

[Fichiers générés par l'Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)<br/>
