---
description: 'En savoir plus sur : notifications de prise en charge'
title: Prise en charge des notifications
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
ms.openlocfilehash: 3f03ded9b900a8691c256e6cde8eaf1a2f4fb5cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316672"
---
# <a name="supporting-notifications"></a>Prise en charge des notifications

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implémentation d’interfaces de point de connexion sur le fournisseur et le consommateur

Pour implémenter des notifications, une classe de fournisseur doit hériter de [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) et de [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).

`IRowsetNotifyCP` implémente le site du fournisseur pour l’interface de point de connexion [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)). `IRowsetNotifyCP` implémente des fonctions de diffusion pour informer les écouteurs sur le point `IID_IRowsetNotify` de connexion des modifications apportées au contenu de l’ensemble de lignes.

Vous devez également implémenter et inscrire `IRowsetNotify` sur le consommateur (également appelé récepteur) à l’aide de [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) afin que le consommateur puisse gérer les notifications. Pour plus d’informations sur l’implémentation de l’interface de point de connexion sur le consommateur, consultez [réception de notifications](../../data/oledb/receiving-notifications.md).

En outre, la classe doit avoir un mappage qui définit l’entrée de point de connexion, comme suit :

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>Ajout de IRowsetNotify

Pour ajouter `IRowsetNotify` , vous devez ajouter `IConnectionPointContainerImpl<rowset-name>` et `IRowsetNotifyCP<rowset-name>` à votre chaîne d’héritage.

Par exemple, voici la chaîne d’héritage pour `RUpdateRowset` dans [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV):

> [!NOTE]
> L’exemple de code peut différer de ce qui est répertorié ici. Considérez cet exemple de code comme la version la plus récente.

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)

class RUpdateRowset :
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,
         CAtlArray< CAgentMan, CAtlArray<CAgentMan>>, CSimpleRow,
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll >>,
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,
      public IConnectionPointContainerImpl<RUpdateRowset>,
      public IRowsetNotifyCP<RUpdateRowset>
```

### <a name="setting-com-map-entries"></a>Définition des entrées de mappage COM

Vous devez également ajouter le code suivant à la table COM dans votre ensemble de lignes :

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

Ces macros permettent à quiconque appelant `QueryInterface` pour votre conteneur de point de connexion (la base de `IRowsetNotify` ) de trouver l’interface demandée sur votre fournisseur. Pour obtenir un exemple d’utilisation des points de connexion, consultez l’exemple et le Didacticiel ATL POLYGON.

### <a name="setting-connection-point-map-entries"></a>Définition des entrées de mappage de point de connexion

Vous devez également ajouter une carte de point de connexion. Voici comment elle devrait se présenter :

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

Cette carte de point de connexion permet à un composant recherchant l’interface de le `IRowsetNotify` trouver dans votre fournisseur.

### <a name="setting-properties"></a>Définition de propriétés

Vous devez également ajouter les propriétés suivantes à votre fournisseur. Vous devez uniquement ajouter des propriétés basées sur les interfaces que vous prenez en charge.

|Propriété|Ajouter si vous prenez en charge|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|Toujours|
|DBPROP_NOTIFICATIONGRANULARITY|Toujours|
|DBPROP_NOTIFICATIONPHASES|Toujours|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|Toujours|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|Toujours|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

La majeure partie de l’implémentation des notifications est déjà incorporée dans les modèles du fournisseur OLE DB. Si vous n’ajoutez pas `IRowsetNotifyCP` à votre chaîne d’héritage, le compilateur supprime tout ce code de votre flux de compilation, ce qui réduit la taille du code.

## <a name="see-also"></a>Voir aussi

[Techniques avancées du fournisseur](../../data/oledb/advanced-provider-techniques.md)
