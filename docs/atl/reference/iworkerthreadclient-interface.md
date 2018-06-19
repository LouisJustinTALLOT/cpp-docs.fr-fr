---
title: Interface de IWorkerThreadClient | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IWorkerThreadClient
- ATLUTIL/ATL::IWorkerThreadClient
- ATLUTIL/ATL::CloseHandle
- ATLUTIL/ATL::Execute
dev_langs:
- C++
helpviewer_keywords:
- IWorkerThreadClient interface
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8336edb07d02bbbcd5775eaf3ef8fe0f735d3adb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359815"
---
# <a name="iworkerthreadclient-interface"></a>Interface de IWorkerThreadClient
`IWorkerThreadClient` est l’interface implémentée par les clients de la [CWorkerThread](../../atl/reference/cworkerthread-class.md) classe.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
__interface IWorkerThreadClient
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CloseHandle](#closehandle)|Implémentez cette méthode pour fermer le handle associé à cet objet.|  
|[Exécuter](#execute)|Implémentez cette méthode pour exécuter du code quand le handle associé à cet objet soit signalé.|  
  
## <a name="remarks"></a>Notes  
 Implémentez cette interface lorsque vous avez du code qui doit s’exécuter sur un thread de travail en réponse à un handle ne soit signalé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlutil.h  
  
##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle  
 Implémentez cette méthode pour fermer le handle associé à cet objet.  
  
```
HRESULT CloseHandle(HANDLE  hHandle);
```  
  
### <a name="parameters"></a>Paramètres  
 *hHandle*  
 Le handle doit être fermé.  
  
### <a name="return-value"></a>Valeur de retour  
 Sur la réussite ou une erreur HRESULT d’échec, retourne S_OK.  
  
### <a name="remarks"></a>Notes  
 Le handle passé à cette méthode a été précédemment associé à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Exemple  
 Le code suivant montre une implémentation simple de `IWorkerThreadClient::CloseHandle`.  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iworkerthreadclient-interface_1.cpp)]  
  
##  <a name="execute"></a>  IWorkerThreadClient::Execute  
 Implémentez cette méthode pour exécuter du code quand le handle associé à cet objet soit signalé.  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwParam`  
 Le paramètre de l’utilisateur.  
  
 `hObject`  
 Le handle a été signalé.  
  
### <a name="return-value"></a>Valeur de retour  
 Sur la réussite ou une erreur HRESULT d’échec, retourne S_OK.  
  
### <a name="remarks"></a>Notes  
 Les handles et DWORD/pointeur passé à cette méthode ont été précédemment associé à cet objet par un appel à [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Exemple  
 Le code suivant montre une implémentation simple de `IWorkerThreadClient::Execute`.  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iworkerthreadclient-interface_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../atl/reference/atl-classes.md)   
 [CWorkerThread, classe](../../atl/reference/cworkerthread-class.md)
