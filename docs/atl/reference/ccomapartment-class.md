---
title: CComApartment, classe
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
ms.openlocfilehash: 5f4c7fc356e61210e9b99bf9989b1bb3f0abc98a
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821673"
---
# <a name="ccomapartment-class"></a>CComApartment, classe

Cette classe fournit la prise en charge de la gestion d’un cloisonnement dans un module EXE mis en pool de threads.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComApartment
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|Constructeur.|

### <a name="public-methods"></a>Méthodes publiques

|Name|Description|
|----------|-----------------|
|[CComApartment::Apartment](#apartment)|Marque l’adresse de début du thread.|
|[CComApartment::GetLockCount](#getlockcount)|Retourne le nombre de verrous actuel du thread.|
|[CComApartment::Lock](#lock)|Incrémente le nombre de verrous du thread.|
|[CComApartment::Unlock](#unlock)|Décrémente le nombre de verrous du thread.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Contient l’identificateur du thread.|
|[CComApartment::m_hThread](#m_hthread)|Contient le handle du thread.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Contient le nombre de verrous actuel du thread.|

## <a name="remarks"></a>Notes

`CComApartment` est utilisé par [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) pour gérer un cloisonnement dans un module exe mis en pool de threads. `CComApartment` fournit des méthodes pour incrémenter et décrémenter le nombre de verrous sur un thread.

## <a name="requirements"></a>Configuration requise pour

**En-tête :** atlbase. h

##  <a name="apartment"></a>  CComApartment::Apartment

Marque l’adresse de début du thread.

```
DWORD Apartment();
```

### <a name="return-value"></a>Valeur de retour

Toujours 0.

### <a name="remarks"></a>Notes

Défini automatiquement pendant [CComAutoThreadModule :: init](../../atl/reference/ccomautothreadmodule-class.md#init).

##  <a name="ccomapartment"></a>  CComApartment::CComApartment

Constructeur.

```
CComApartment();
```

### <a name="remarks"></a>Notes

Initialise le `CComApartment` membres de données [m_nLockCnt](#m_nlockcnt) et [m_hThread](#m_hthread).

##  <a name="getlockcount"></a>  CComApartment::GetLockCount

Retourne le nombre de verrous actuel du thread.

```
LONG GetLockCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre de verrous sur le thread.

##  <a name="lock"></a>  CComApartment::Lock

Incrémente le nombre de verrous du thread.

```
LONG Lock();
```

### <a name="return-value"></a>Valeur de retour

Valeur qui peut être utile pour les diagnostics ou les tests.

### <a name="remarks"></a>Notes

Appelé par [CComAutoThreadModule :: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).

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

Contient le nombre de verrous actuel du thread.

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>  CComApartment::Unlock

Décrémente le nombre de verrous du thread.

```
LONG Unlock();
```

### <a name="return-value"></a>Valeur de retour

Valeur qui peut être utile pour les diagnostics ou les tests.

### <a name="remarks"></a>Notes

Appelé par [CComAutoThreadModule :: Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Le nombre de verrous sur le thread est utilisé à des fins statistiques.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
