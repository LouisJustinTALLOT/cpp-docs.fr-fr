---
title: CriticalSection (classe)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
ms.openlocfilehash: b95e512f89ee1ff32ca9f1bea51bce643d185a2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220520"
---
# <a name="criticalsection-class"></a>CriticalSection (classe)

Représente un objet de section critique.

## <a name="syntax"></a>Syntaxe

```cpp
class CriticalSection;
```

## <a name="members"></a>Membres

### <a name="constructor"></a>Constructeur

Nom                                                        | Description
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection :: CriticalSection](#criticalsection)        | Initialise un objet de synchronisation qui est semblable à un objet mutex, mais qui peut être utilisé uniquement par les threads d’un processus unique.
[CriticalSection :: ~ CriticalSection](#tilde-criticalsection) | Déinitialise et détruit l' `CriticalSection` objet actuel.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                 | Description
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection :: IsValid](#isvalid) | Indique si la section critique actuelle est valide.
[CriticalSection :: Lock](#lock)       | Attend la propriété de l’objet de section critique spécifié. La fonction retourne lorsque la propriété est accordée au thread appelant.
[CriticalSection :: TryLock,](#trylock) | Tente d’entrer dans une section critique sans blocage. Si l’appel réussit, le thread appelant prend possession de la section critique.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                        | Description
--------------------------- | ----------------------------------------
[CriticalSection :: cs_](#cs) | Déclare un membre de données de section critique.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CriticalSection`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>CriticalSection :: ~ CriticalSection

Déinitialise et détruit l' `CriticalSection` objet actuel.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>CriticalSection :: CriticalSection

Initialise un objet de synchronisation qui est semblable à un objet mutex, mais qui peut être utilisé uniquement par les threads d’un processus unique.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Paramètres

*spincount*<br/>
Nombre de spins pour l’objet de section critique. La valeur par défaut est 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les sections critiques et les spincounts, consultez la `InitializeCriticalSectionAndSpinCount` fonction dans la `Synchronization` section de l’API Windows documentation.

## <a name="criticalsectioncs_"></a><a name="cs"></a>CriticalSection :: cs_

Déclare un membre de données de section critique.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Notes

Ce membre de données est protégé.

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>CriticalSection :: IsValid

Indique si la section critique actuelle est valide.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

Par défaut, retourne toujours **`true`** .

## <a name="criticalsectionlock"></a><a name="lock"></a>CriticalSection :: Lock

Attend la propriété de l’objet de section critique spécifié. La fonction retourne lorsque la propriété est accordée au thread appelant.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Objet de section critique spécifié par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

Objet Lock qui peut être utilisé pour déverrouiller la section critique actuelle.

### <a name="remarks"></a>Notes

La première `Lock` fonction affecte l’objet de section critique actuel. La deuxième `Lock` fonction affecte une section critique spécifiée par l’utilisateur.

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>CriticalSection :: TryLock,

Tente d’entrer dans une section critique sans blocage. Si l’appel réussit, le thread appelant prend possession de la section critique.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Objet de section critique spécifié par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si la section critique est entrée correctement ou si le thread actuel possède déjà la section critique. Zéro si un autre thread possède déjà la section critique.

### <a name="remarks"></a>Notes

La première `TryLock` fonction affecte l’objet de section critique actuel. La deuxième `TryLock` fonction affecte une section critique spécifiée par l’utilisateur.
