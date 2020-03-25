---
title: Réception des notifications
ms.date: 10/24/2018
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
ms.openlocfilehash: 4b630a9728770a5e35e6d6300cf465b90238350c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209777"
---
# <a name="receiving-notifications"></a>Réception des notifications

OLE DB fournit des interfaces pour recevoir des notifications lorsque des événements se produisent. Celles-ci sont décrites dans [OLE DB les notifications d’objets](/previous-versions/windows/desktop/ms725406(v=vs.85)) dans le **Guide de référence du programmeur OLE DB**. La configuration de ces événements utilise le mécanisme de point de connexion COM standard. Par exemple, un objet ATL qui souhaite récupérer des événements via `IRowsetNotify` implémente l’interface `IRowsetNotify` en ajoutant `IRowsetNotify` à la liste dérivée de la classe et en l’exposant via une macro COM_INTERFACE_ENTRY.

`IRowsetNotify` a trois méthodes, qui peuvent être appelées à différents moments. Si vous souhaitez répondre à une seule de ces méthodes, vous pouvez utiliser la classe [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) , qui retourne E_NOTIMPL pour les méthodes qui ne vous intéressent pas.

Lorsque vous créez l’ensemble de lignes, vous devez indiquer au fournisseur que l’objet d’ensemble de lignes retourné doit prendre en charge `IConnectionPointContainer`, ce qui est nécessaire pour configurer la notification.

Le code suivant montre comment ouvrir l’ensemble de lignes à partir d’un objet ATL et utiliser la fonction `AtlAdvise` pour configurer le récepteur de notifications. `AtlAdvise` retourne un cookie qui est utilisé lorsque vous appelez `AtlUnadvise`.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

Ensuite, utilisé par le code suivant :

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)
