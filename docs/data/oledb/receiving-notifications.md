---
title: Recevoir des Notifications | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 554090aadd9090e813a17d6b967ad6acbf92d924
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083578"
---
# <a name="receiving-notifications"></a>Réception des notifications

OLE DB fournit des interfaces pour recevoir des notifications lorsque des événements se produisent. Ceux-ci sont décrits dans [Notifications de l’objet OLE DB](/previous-versions/windows/desktop/ms725406) dans le *de référence du programmeur OLE DB*. Le programme d’installation de ces événements utilise le mécanisme de point de connexion COM standard. Par exemple, un objet ATL qui souhaite récupérer des événements via `IRowsetNotify` implémente le `IRowsetNotify` interface en ajoutant `IRowsetNotify` à la liste de classe dérivée et en l’exposant via une macro COM_INTERFACE_ENTRY.  
  
`IRowsetNotify` a trois méthodes, qui peuvent être appelées à différents moments. Si vous souhaitez répondre à une seule de ces méthodes, vous pouvez utiliser la [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) (classe), qui retourne E_NOTIMPL pour les méthodes que vous n’êtes pas intéressé.  
  
Lorsque vous créez l’ensemble de lignes, vous devez indiquer au fournisseur que vous souhaitez l’objet d’ensemble de lignes retourné pour prendre en charge `IConnectionPointContainer`, qui est nécessaire pour configurer la notification.  
  
Le code suivant montre comment ouvrir l’ensemble de lignes à partir d’un objet ATL et utiliser le `AtlAdvise` (fonction) pour configurer le récepteur de notification. `AtlAdvise` Retourne un cookie qui est utilisé lorsque vous appelez `AtlUnadvise`.  
  
```cpp  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  
product.Open(session, _T("Products"), &propset);  
  
AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## <a name="see-also"></a>Voir aussi  

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)