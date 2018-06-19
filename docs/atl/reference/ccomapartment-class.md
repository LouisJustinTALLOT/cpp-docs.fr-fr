---
title: Classe de CComApartment | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
dev_langs:
- C++
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88e08d50cec36366df2423d31082b97d41b5061f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362159"
---
# <a name="ccomapartment-class"></a>Classe de CComApartment
Cette classe prend en charge la gestion d’un appartement dans un module EXE mis en pool de threads.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComApartment
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComApartment::CComApartment](#ccomapartment)|Constructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComApartment::Apartment](#apartment)|Marque l’adresse de départ du thread.|  
|[CComApartment::GetLockCount](#getlockcount)|Retourne le nombre de verrous du thread actuel.|  
|[CComApartment::Lock](#lock)|Incrémente le nombre de verrous du thread.|  
|[CComApartment::Unlock](#unlock)|Décrémente de nombre de verrous du thread.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Contient l’identificateur de la thread.|  
|[CComApartment::m_hThread](#m_hthread)|Contient le handle du thread.|  
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Contient le nombre de verrous du thread actuel.|  
  
## <a name="remarks"></a>Notes  
 `CComApartment` est utilisé par [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) pour gérer un thread cloisonné dans un module EXE mis en pool de threads. `CComApartment` Fournit des méthodes pour incrémenter et décrémenter le verrou comptent sur un thread.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
##  <a name="apartment"></a>  CComApartment::Apartment  
 Marque l’adresse de départ du thread.  
  
```
DWORD Apartment();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Toujours 0.  
  
### <a name="remarks"></a>Notes  
 Définir automatiquement au cours de [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).  
  
##  <a name="ccomapartment"></a>  CComApartment::CComApartment  
 Constructeur.  
  
```
CComApartment();
```  
  
### <a name="remarks"></a>Notes  
 Initialise le `CComApartment` membres de données [m_nLockCnt](#m_nlockcnt) et [m_hThread](#m_hthread).  
  
##  <a name="getlockcount"></a>  CComApartment::GetLockCount  
 Retourne le nombre de verrous du thread actuel.  
  
```
LONG GetLockCount();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de verrous sur le thread.  
  
##  <a name="lock"></a>  CComApartment::Lock  
 Incrémente le nombre de verrous du thread.  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut être utile pour les tests de diagnostic ou de test.  
  
### <a name="remarks"></a>Notes  
 Appelé par [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).  
  
 Le nombre de verrous sur le thread est utilisé à des fins statistiques.  
  
##  <a name="m_dwthreadid"></a>  CComApartment::m_dwThreadID  
 Contient l’identificateur de la thread.  
  
```
DWORD m_dwThreadID;
```  
  
##  <a name="m_hthread"></a>  CComApartment::m_hThread  
 Contient le handle du thread.  
  
```
HANDLE m_hThread;
```  
  
##  <a name="m_nlockcnt"></a>  CComApartment::m_nLockCnt  
 Contient le nombre de verrous du thread actuel.  
  
```
LONG m_nLockCnt;
```  
  
##  <a name="unlock"></a>  CComApartment::Unlock  
 Décrémente de nombre de verrous du thread.  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut être utile pour les tests de diagnostic ou de test.  
  
### <a name="remarks"></a>Notes  
 Appelé par [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).  
  
 Le nombre de verrous sur le thread est utilisé à des fins statistiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
