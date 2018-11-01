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
ms.openlocfilehash: dd34206741ba8fee8b283e22b6e8eefb3b3efb0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651150"
---
# <a name="criticalsection-class"></a>CriticalSection (classe)

Représente un objet de section critique.

## <a name="syntax"></a>Syntaxe

```cpp
class CriticalSection;
```

## <a name="members"></a>Membres

### <a name="constructor"></a>Constructeur

Name                                                        | Description
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::CriticalSection](#criticalsection)        | Initialise un objet de synchronisation qui est similaire à un objet mutex, mais peut être utilisé par uniquement les threads d’un processus unique.
[CriticalSection :: ~ CriticalSection](#tilde-criticalsection) | Annule l’initialisation et détruit actuel `CriticalSection` objet.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                 | Description
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::IsValid](#isvalid) | Indique si la section critique en cours est valide.
[CriticalSection::Lock](#lock)       | Attend que la propriété de l’objet de section critique spécifié. La fonction retourne quand le thread appelant est accordé à la propriété.
[CriticalSection::TryLock](#trylock) | Tentatives de saisie d’une section critique sans bloquer. Si l’appel réussit, le thread appelant prend possession de la section critique.

### <a name="protected-data-members"></a>Membres de données protégés

Name                        | Description
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | Déclare un membre de données de section critique.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CriticalSection`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="tilde-criticalsection"></a>CriticalSection :: ~ CriticalSection

Annule l’initialisation et détruit actuel `CriticalSection` objet.

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsection"></a>CriticalSection::CriticalSection

Initialise un objet de synchronisation qui est similaire à un objet mutex, mais peut être utilisé par uniquement les threads d’un processus unique.

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Paramètres

*spinCount*<br/>
Nombre de spins pour l’objet de section critique. La valeur par défaut est 0.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les sections critiques et spincounts, consultez le `InitializeCriticalSectionAndSpinCount` fonctionner dans la `Synchronization` section de la documentation de l’API de Windows.

## <a name="cs"></a>CriticalSection::cs_

Déclare un membre de données de section critique.

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>Notes

Ce membre de données est protégé.

## <a name="isvalid"></a>CriticalSection::IsValid

Indique si la section critique en cours est valide.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Valeur de retour

Par défaut, retourne toujours **true**.

## <a name="lock"></a>CriticalSection::Lock

Attend que la propriété de l’objet de section critique spécifié. La fonction retourne quand le thread appelant est accordé à la propriété.

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Paramètres

*cs*<br/>
Un objet spécifié par l’utilisateur de section critique.

### <a name="return-value"></a>Valeur de retour

Un objet de verrouillage qui peut être utilisé pour déverrouiller la section critique en cours.

### <a name="remarks"></a>Notes

Le premier `Lock` fonction affecte l’objet en cours de la section critique. La seconde `Lock` fonction affecte une section critique spécifié par l’utilisateur.

## <a name="trylock"></a>CriticalSection::TryLock

Tentatives de saisie d’une section critique sans bloquer. Si l’appel réussit, le thread appelant prend possession de la section critique.

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Paramètres

*cs*<br/>
Un objet spécifié par l’utilisateur de section critique.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la section critique est entrée avec succès ou le thread actif possède déjà la section critique. Zéro si un autre thread possède déjà la section critique.

### <a name="remarks"></a>Notes

Le premier `TryLock` fonction affecte l’objet en cours de la section critique. La seconde `TryLock` fonction affecte une section critique spécifié par l’utilisateur.
