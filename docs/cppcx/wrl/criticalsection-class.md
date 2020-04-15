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
ms.openlocfilehash: 5deb89e795d1886ca316886ae1ea260ce1f36fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372587"
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
[CriticalSection::CriticalSection](#criticalsection)        | Initialise un objet de synchronisation similaire à un objet mutex, mais qui ne peut être utilisé que par les fils d’un seul processus.
[CriticalSection::-CriticalSection](#tilde-criticalsection) | Désinitialise et détruit l’objet actuel. `CriticalSection`

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                 | Description
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::IsValid](#isvalid) | Indique si la section critique actuelle est valide.
[CriticalSection::Lock](#lock)       | Attend la propriété de l’objet de section critique spécifié. La fonction revient lorsque le fil d’appel est accordé la propriété.
[CriticalSection::TryLock](#trylock) | Tentatives d’entrer dans une section critique sans bloquer. Si l’appel est réussi, le fil d’appel s’approprie la section critique.

### <a name="protected-data-members"></a>Membres de données protégés

Nom                        | Description
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | Déclare un membre critique des données de section.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CriticalSection`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>CriticalSection::-CriticalSection

Désinitialise et détruit l’objet actuel. `CriticalSection`

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>CriticalSection::CriticalSection

Initialise un objet de synchronisation similaire à un objet mutex, mais qui ne peut être utilisé que par les fils d’un seul processus.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Paramètres

*spincount*<br/>
Le nombre de spins pour l’objet de section critique. La valeur par défaut est 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les sections `InitializeCriticalSectionAndSpinCount` critiques `Synchronization` et les spincounts, voir la fonction dans la section de la documenation De l’API Windows.

## <a name="criticalsectioncs_"></a><a name="cs"></a>CriticalSection::cs_

Déclare un membre critique des données de section.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Notes

Ce membre des données est protégé.

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>CriticalSection::IsValid

Indique si la section critique actuelle est valide.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

Par défaut, retourne toujours **vrai**.

## <a name="criticalsectionlock"></a><a name="lock"></a>CriticalSection::Lock

Attend la propriété de l’objet de section critique spécifié. La fonction revient lorsque le fil d’appel est accordé la propriété.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Paramètres

*Cs*<br/>
Objet de section critique spécifié par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

Un objet de verrouillage qui peut être utilisé pour déverrouiller la section critique actuelle.

### <a name="remarks"></a>Notes

La `Lock` première fonction affecte l’objet de section critique actuel. La `Lock` deuxième fonction affecte une section critique spécifiée par l’utilisateur.

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>CriticalSection::TryLock

Tentatives d’entrer dans une section critique sans bloquer. Si l’appel est réussi, le fil d’appel s’approprie la section critique.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Paramètres

*Cs*<br/>
Objet de section critique spécifié par l’utilisateur.

### <a name="return-value"></a>Valeur de retour

Une valeur non zéro si la section critique est saisie avec succès ou si le thread actuel possède déjà la section critique. Zéro si un autre thread possède déjà la section critique.

### <a name="remarks"></a>Notes

La `TryLock` première fonction affecte l’objet de section critique actuel. La `TryLock` deuxième fonction affecte une section critique spécifiée par l’utilisateur.
