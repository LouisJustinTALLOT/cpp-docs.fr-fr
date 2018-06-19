---
title: IRowsetNotifyImpl, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 860b735863acbcac869a4a297984084946aaf028
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106256"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl, classe
Implémente et enregistre [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) sur le consommateur (également appelé « récepteur ») afin qu’il puisse gérer les notifications.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[OnFieldChange](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|Notifie le consommateur de toute modification apportée à la valeur d’une colonne.|  
|[OnRowChange](../../data/oledb/irowsetnotifyimpl-onrowchange.md)|Notifie le consommateur de la première modification à une ligne ou d’une modification qui affecte la ligne entière.|  
|[OnRowsetChange](../../data/oledb/irowsetnotifyimpl-onrowsetchange.md)|Notifie le consommateur de toute modification qui affecte l’ensemble de lignes.|  
  
## <a name="remarks"></a>Notes  
 Consultez [réception des Notifications](../../data/oledb/receiving-notifications.md) sur l’implémentation de l’interface de point de connexion sur le consommateur.  
  
 `IRowsetNotifyImpl` Fournit une implémentation factice pour `IRowsetNotify`, avec des fonctions vides pour le `IRowsetNotify` méthodes [OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx), [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx), et [OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx). Si vous héritez de cette classe lorsque vous implémentez un `IRowsetNotify` interface, vous pouvez implémenter uniquement les méthodes que vous avez besoin. Vous devez également fournir des implémentations vides pour les autres méthodes vous-même.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)   
 [IRowsetNotifyCP, classe](../../data/oledb/irowsetnotifycp-class.md)