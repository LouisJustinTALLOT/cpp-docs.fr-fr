---
title: Classe CComFakeCriticalSection
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
ms.openlocfilehash: 4a5b9ba3551397a9c3d59a343e9c6b55b1c1207e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327851"
---
# <a name="ccomfakecriticalsection-class"></a>Classe CComFakeCriticalSection

Cette classe fournit les mêmes méthodes que [CComCriticalSection,](../../atl/reference/ccomcriticalsection-class.md) mais ne fournit pas une section critique.

## <a name="syntax"></a>Syntaxe

```
class CComFakeCriticalSection
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComFakeCriticalSection::Init](#init)|Ne fait rien puisqu’il n’y a pas de section critique.|
|[CComFakeCriticalSection::Lock](#lock)|Ne fait rien puisqu’il n’y a pas de section critique.|
|[CComFakeCriticalSection::Terme](#term)|Ne fait rien puisqu’il n’y a pas de section critique.|
|[CComFakeCriticalSection::Unlock](#unlock)|Ne fait rien puisqu’il n’y a pas de section critique.|

## <a name="remarks"></a>Notes

`CComFakeCriticalSection`reflète les méthodes trouvées dans [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Toutefois, `CComFakeCriticalSection` ne fournit pas de section critique; par conséquent, ses méthodes ne font rien.

Typiquement, vous `CComFakeCriticalSection` utilisez `typedef` par `AutoCriticalSection` le `CriticalSection`biais d’un nom, soit ou . Lors de l’utilisation [de CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) ou [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), ces `typedef` deux noms de référence `CComFakeCriticalSection`. Lors de l’utilisation [de CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), `CComCriticalSection`ils font référence À [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) et, respectivement.

## <a name="requirements"></a>Spécifications

**En-tête:** atlcore.h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>CComFakeCriticalSection::Init

Ne fait rien puisqu’il n’y a pas de section critique.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>CComFakeCriticalSection::Lock

Ne fait rien puisqu’il n’y a pas de section critique.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>CComFakeCriticalSection::Terme

Ne fait rien puisqu’il n’y a pas de section critique.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>CComFakeCriticalSection::Unlock

Ne fait rien puisqu’il n’y a pas de section critique.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
