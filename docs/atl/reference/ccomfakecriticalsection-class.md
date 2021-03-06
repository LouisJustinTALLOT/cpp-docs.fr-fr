---
description: 'En savoir plus sur : classe CComFakeCriticalSection'
title: CComFakeCriticalSection, classe
ms.date: 11/04/2016
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
ms.openlocfilehash: 7280a47daa7464b24246ca8baa0aa7f5eaefa87a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152059"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection, classe

Cette classe fournit les mêmes méthodes que [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) , mais ne fournit pas de section critique.

## <a name="syntax"></a>Syntaxe

```
class CComFakeCriticalSection
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComFakeCriticalSection :: init](#init)|Ne fait rien, car il n’existe pas de section critique.|
|[CComFakeCriticalSection :: Lock](#lock)|Ne fait rien, car il n’existe pas de section critique.|
|[CComFakeCriticalSection :: term](#term)|Ne fait rien, car il n’existe pas de section critique.|
|[CComFakeCriticalSection :: Unlock](#unlock)|Ne fait rien, car il n’existe pas de section critique.|

## <a name="remarks"></a>Notes

`CComFakeCriticalSection` reflète les méthodes trouvées dans [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Toutefois, `CComFakeCriticalSection` ne fournit pas de section critique ; par conséquent, ses méthodes ne font rien.

En général, vous utilisez `CComFakeCriticalSection` un **`typedef`** nom, `AutoCriticalSection` ou `CriticalSection` . Si vous utilisez [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), ces deux **`typedef`** noms font référence `CComFakeCriticalSection` . Lors de l’utilisation de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), ils référencent [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) et `CComCriticalSection` , respectivement.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a> CComFakeCriticalSection :: init

Ne fait rien, car il n’existe pas de section critique.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a> CComFakeCriticalSection :: Lock

Ne fait rien, car il n’existe pas de section critique.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a> CComFakeCriticalSection :: term

Ne fait rien, car il n’existe pas de section critique.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a> CComFakeCriticalSection :: Unlock

Ne fait rien, car il n’existe pas de section critique.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
