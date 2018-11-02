---
title: Ccomcritseclock, classe
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
ms.openlocfilehash: e0f68f48867510c270c7c69e325a796f274198d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606997"
---
# <a name="ccomcritseclock-class"></a>Ccomcritseclock, classe

Cette classe fournit des méthodes de verrouillage et déverrouillage d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Paramètres

*TLock*<br/>
Objet à être verrouillées et déverrouillées.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|Constructeur.|
|[CComCritSecLock :: ~ CComCritSecLock](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|Appelez cette méthode pour verrouiller l’objet de section critique.|
|[CComCritSecLock::Unlock](#unlock)|Appelez cette méthode pour déverrouiller l’objet de section critique.|

## <a name="remarks"></a>Notes

Utilisez cette classe pour verrouiller et déverrouiller des objets de façon plus sûre qu’avec le [CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md) ou [ccomautocriticalsection, classe](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase.h

##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock

Constructeur.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Paramètres

*cs*<br/>
L’objet de section critique.

*bInitialLock*<br/>
L’état de verrouillage initial : **true** signifie verrouillé.

### <a name="remarks"></a>Notes

Initialise l’objet de section critique.

##  <a name="dtor"></a>  CComCritSecLock :: ~ CComCritSecLock

Destructeur.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Notes

Déverrouille l’objet de section critique.

##  <a name="lock"></a>  CComCritSecLock::Lock

Appelez cette méthode pour verrouiller l’objet de section critique.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valeur de retour

En cas d’échec, retourne S_OK si l’objet a correctement été verrouillé, ou une erreur HRESULT.

### <a name="remarks"></a>Notes

Si l’objet est déjà verrouillé, une erreur d’assertion se produit dans les versions debug.

##  <a name="unlock"></a>  CComCritSecLock::Unlock

Appelez cette méthode pour déverrouiller l’objet de section critique.

```
void Unlock() throw();
```

### <a name="remarks"></a>Notes

Si l’objet est déjà déverrouillé, une erreur d’assertion se produit dans les versions debug.

## <a name="see-also"></a>Voir aussi

[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection, classe](../../atl/reference/ccomautocriticalsection-class.md)
