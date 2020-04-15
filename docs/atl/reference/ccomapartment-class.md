---
title: Classe CComApartment
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
ms.openlocfilehash: 13141d27592f6f40ea7b0529c61baba2fe83a10a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321116"
---
# <a name="ccomapartment-class"></a>Classe CComApartment

Cette classe fournit un soutien pour la gestion d’un appartement dans un module EXE en fil commun.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CComApartment::Appartement](#apartment)|Marque l’adresse de départ du thread.|
|[CComApartment::GetLockCount](#getlockcount)|Retourne le nombre de verrous actuel du thread.|
|[CComApartment::Lock](#lock)|Incréments le nombre de serrures du fil.|
|[CComApartment::Unlock](#unlock)|Décrément le nombre de serrures du fil.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Contient l’identifiant du thread.|
|[CComApartment::m_hThread](#m_hthread)|Contient la poignée du thread.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Contient le nombre de verrous actuel du fil.|

## <a name="remarks"></a>Notes

`CComApartment`est utilisé par [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) pour gérer un appartement dans un module EXE en fil commun. `CComApartment`fournit des méthodes pour incrémenter et décroisser le compte de verrouillage sur un thread.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomapartmentapartment"></a><a name="apartment"></a>CComApartment::Appartement

Marque l’adresse de départ du thread.

```
DWORD Apartment();
```

### <a name="return-value"></a>Valeur de retour

Toujours 0.

### <a name="remarks"></a>Notes

Automatiquement réglé pendant [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init).

## <a name="ccomapartmentccomapartment"></a><a name="ccomapartment"></a>CComApartment::CComApartment

Constructeur.

```
CComApartment();
```

### <a name="remarks"></a>Notes

Initialise les `CComApartment` [données](#m_nlockcnt) m_nLockCnt et [m_hThread](#m_hthread).

## <a name="ccomapartmentgetlockcount"></a><a name="getlockcount"></a>CComApartment::GetLockCount

Retourne le nombre de verrous actuel du thread.

```
LONG GetLockCount();
```

### <a name="return-value"></a>Valeur de retour

Le verrou compte sur le fil.

## <a name="ccomapartmentlock"></a><a name="lock"></a>CComApartment::Lock

Incréments le nombre de serrures du fil.

```
LONG Lock();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic ou les tests.

### <a name="remarks"></a>Notes

Appelé par [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Le compte de verrouillage sur le thread est utilisé à des fins statistiques.

## <a name="ccomapartmentm_dwthreadid"></a><a name="m_dwthreadid"></a>CComApartment::m_dwThreadID

Contient l’identifiant du thread.

```
DWORD m_dwThreadID;
```

## <a name="ccomapartmentm_hthread"></a><a name="m_hthread"></a>CComApartment::m_hThread

Contient la poignée du thread.

```
HANDLE m_hThread;
```

## <a name="ccomapartmentm_nlockcnt"></a><a name="m_nlockcnt"></a>CComApartment::m_nLockCnt

Contient le nombre de verrous actuel du fil.

```
LONG m_nLockCnt;
```

## <a name="ccomapartmentunlock"></a><a name="unlock"></a>CComApartment::Unlock

Décrément le nombre de serrures du fil.

```
LONG Unlock();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui peut être utile pour le diagnostic ou les tests.

### <a name="remarks"></a>Notes

Appelé par [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Le compte de verrouillage sur le thread est utilisé à des fins statistiques.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
