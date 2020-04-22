---
title: Classe CComCritSecLock
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: 4b2ef093c1142b592ad2a6605a08bd8c34a643ea
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748076"
---
# <a name="ccomcritseclock-class"></a>Classe CComCritSecLock

Cette classe fournit des méthodes pour verrouiller et déverrouiller un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Paramètres

*TLock TLock*<br/>
L’objet à verrouiller et déverrouillé.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|Constructeur.|
|[CComCritSecLock::CComCritSecLock](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|Appelez cette méthode pour verrouiller l’objet de section critique.|
|[CComCritSecLock::Unlock](#unlock)|Appelez cette méthode pour déverrouiller l’objet de section critique.|

## <a name="remarks"></a>Notes

Utilisez cette classe pour verrouiller et déverrouiller des objets d’une manière plus sûre qu’avec la [classe CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ou [la classe CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock::CComCritSecLock

Constructeur.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Paramètres

*Cs*<br/>
L’objet de section critique.

*bInitialLock (en)*<br/>
L’état de verrouillage initial : **véritable** moyen verrouillé.

### <a name="remarks"></a>Notes

Initialise l’objet de section critique.

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock::CComCritSecLock

Destructeur.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Notes

Déverrouiller l’objet de section critique.

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock::Lock

Appelez cette méthode pour verrouiller l’objet de section critique.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK si l’objet a été verrouillé avec succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Si l’objet est déjà verrouillé, une erreur ASSERT se produira dans les constructions de débogé.

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock::Unlock

Appelez cette méthode pour déverrouiller l’objet de section critique.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Notes

Si l’objet est déjà déverrouillé, une erreur ASSERT se produira dans les constructions de débogé.

## <a name="see-also"></a>Voir aussi

[Classe CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Classe CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)
