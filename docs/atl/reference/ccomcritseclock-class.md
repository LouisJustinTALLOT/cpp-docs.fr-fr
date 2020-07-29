---
title: CComCritSecLock, classe
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
ms.openlocfilehash: fd2904f67d84db42d6b35aa4e505b063d6ea9a9f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224290"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock, classe

Cette classe fournit des méthodes pour le verrouillage et le déverrouillage d’un objet de section critique.

## <a name="syntax"></a>Syntaxe

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>Paramètres

*TLock*<br/>
Objet à verrouiller et à déverrouiller.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|Constructeur.|
|[CComCritSecLock :: ~ CComCritSecLock](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComCritSecLock :: Lock](#lock)|Appelez cette méthode pour verrouiller l’objet de section critique.|
|[CComCritSecLock :: Unlock](#unlock)|Appelez cette méthode pour déverrouiller l’objet de section critique.|

## <a name="remarks"></a>Notes

Utilisez cette classe pour verrouiller et déverrouiller des objets de manière plus sécurisée qu’avec la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ou la [classe CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock::CComCritSecLock

Constructeur.

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Objet de section critique.

*bInitialLock*<br/>
L’état initial du verrouillage : **`true`** signifie verrouillé.

### <a name="remarks"></a>Notes

Initialise l’objet de section critique.

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock :: ~ CComCritSecLock

Destructeur.

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Notes

Déverrouille l’objet de section critique.

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock :: Lock

Appelez cette méthode pour verrouiller l’objet de section critique.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne S_OK si l’objet a été verrouillé correctement, ou une erreur HRESULT en cas d’échec.

### <a name="remarks"></a>Notes

Si l’objet est déjà verrouillé, une erreur d’assertion se produit dans les versions Debug.

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock :: Unlock

Appelez cette méthode pour déverrouiller l’objet de section critique.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Notes

Si l’objet est déjà déverrouillé, une erreur d’assertion se produit dans les versions Debug.

## <a name="see-also"></a>Voir aussi

[CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection, classe](../../atl/reference/ccomautocriticalsection-class.md)
