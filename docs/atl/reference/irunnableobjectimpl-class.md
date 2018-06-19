---
title: Classe de IRunnableObjectImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
dev_langs:
- C++
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a08fec0fd38e30729c9131def1831e5e5d8f633e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364113"
---
# <a name="irunnableobjectimpl-class"></a>Classe de IRunnableObjectImpl
Cette classe implémente **IUnknown** et fournit une implémentation par défaut de la [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) interface.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IRunnableObjectImpl
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IRunnableObjectImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Retourne le CLSID du contrôle en cours d’exécution. L’implémentation ATL définit le CLSID `GUID_NULL` et retourne **E_UNEXPECTED**.|  
|[IRunnableObjectImpl::IsRunning](#isrunning)|Détermine si le contrôle est en cours d’exécution. L’implémentation ATL retourne **TRUE**.|  
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Verrouille le contrôle à l’état en cours d’exécution. L’implémentation ATL retourne `S_OK`.|  
|[IRunnableObjectImpl::Run](#run)|Force le contrôle à exécuter. L’implémentation ATL retourne `S_OK`.|  
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indique que le contrôle est incorporé. L’implémentation ATL retourne `S_OK`.|  
  
## <a name="remarks"></a>Notes  
 Le [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) interface permet à un conteneur déterminer si un contrôle est en cours d’exécution, de le forcer à exécuter ou verrouiller dans l’état en cours d’exécution. Classe `IRunnableObjectImpl` fournit une implémentation par défaut de cette interface et implémente **IUnknown** en envoyant des informations pour le vidage de builds périphérique en mode débogage.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass  
 Retourne le CLSID du contrôle en cours d’exécution.  
  
```
HRESULT GetRunningClass(LPCLSID lpClsid);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Les jeux d’implémentation ATL \* *lpClsid* à `GUID_NULL` et retourne **E_UNEXPECTED**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IRunnableObject::GetRunningClass](http://msdn.microsoft.com/library/windows/desktop/ms693734) dans le Kit de développement logiciel Windows.  
  
##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning  
 Détermine si le contrôle est en cours d’exécution.  
  
```
virtual BOOL IsRunning();
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation ATL retourne **TRUE**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IRunnableObject::IsRunning](http://msdn.microsoft.com/library/windows/desktop/ms678496) dans le Kit de développement logiciel Windows.  
  
##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning  
 Verrouille le contrôle à l’état en cours d’exécution.  
  
```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation ATL retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Consultez [IRunnableObject::LockRunning](http://msdn.microsoft.com/library/windows/desktop/ms693361) dans le Kit de développement logiciel Windows.  
  
##  <a name="run"></a>  IRunnableObjectImpl::Run  
 Force le contrôle à exécuter.  
  
```
HRESULT Run(LPBINDCTX lpbc);
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation ATL retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Consultez [IRunnableObject::Run](http://msdn.microsoft.com/library/windows/desktop/ms694517) dans le Kit de développement logiciel Windows.  
  
##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject  
 Indique que le contrôle est incorporé.  
  
```
HRESULT SetContainedObject(BOOL fContained);
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’implémentation ATL retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Consultez [IRunnableObject::SetContainedObject](http://msdn.microsoft.com/library/windows/desktop/ms693710) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
