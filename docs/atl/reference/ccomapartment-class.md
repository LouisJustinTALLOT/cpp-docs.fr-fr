---
title: Ccomapartment, classe
ms.date: 11/04/2016
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
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
ms.openlocfilehash: 92db42a45a0863f8b43f7c46da9624e424d1e488
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290103"
---
# <a name="ccomapartment-class"></a>Ccomapartment, classe

Cette classe prend en charge la gestion d’un cloisonnement dans un module EXE mis en pool de thread.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CComApartment::Unlock](#unlock)|Décrémente de nombre de verrou du thread.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Contient l’identificateur du thread.|
|[CComApartment::m_hThread](#m_hthread)|Contient le handle du thread.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Contient le nombre de verrous du thread actuel.|

## <a name="remarks"></a>Notes

`CComApartment` est utilisé par [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) pour gérer un thread cloisonné dans un module EXE mis en pool de thread. `CComApartment` Fournit des méthodes pour incrémenter et décrémenter le verrou compter sur un thread.

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

Automatiquement définies pendant [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).

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

Une valeur qui peut-être être utiles pour le diagnostic ou de test.

### <a name="remarks"></a>Notes

Appelé par [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Le nombre de verrous sur le thread est utilisé à des fins statistiques.

##  <a name="m_dwthreadid"></a>  CComApartment::m_dwThreadID

Contient l’identificateur du thread.

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

Décrémente de nombre de verrou du thread.

```
LONG Unlock();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut-être être utiles pour le diagnostic ou de test.

### <a name="remarks"></a>Notes

Appelé par [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Le nombre de verrous sur le thread est utilisé à des fins statistiques.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
