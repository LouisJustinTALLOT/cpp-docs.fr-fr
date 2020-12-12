---
description: 'En savoir plus sur : structure CriticalSectionTraits'
title: CriticalSectionTraits (structure)
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: 20e4b7dd47acf6f632c888c9bfdedeb3f4e60270
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272940"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits (structure)

Spécialise un `CriticalSection` objet pour prendre en charge une section critique non valide ou une fonction pour libérer une section critique.

## <a name="syntax"></a>Syntaxe

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | **`typedef`** Qui définit un pointeur vers une section critique. `Type` est défini comme `typedef CRITICAL_SECTION* Type;`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                       | Description
---------------------------------------------------------- | -----------------
[CriticalSectionTraits :: Getinvalidvalue,](#getinvalidvalue) | Spécialise un `CriticalSection` modèle afin que le modèle soit toujours non valide.
[CriticalSectionTraits :: Unlock](#unlock)                   | Spécialise un `CriticalSection` modèle afin qu’il prenne en charge la libération de la propriété de l’objet de section critique spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CriticalSectionTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers :: HandleTraits

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a> CriticalSectionTraits :: Getinvalidvalue,

Spécialise un `CriticalSection` modèle afin que le modèle soit toujours non valide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours un pointeur vers une section critique non valide.

### <a name="remarks"></a>Notes

Le `Type` modificateur est défini comme `typedef CRITICAL_SECTION* Type;` .

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a> CriticalSectionTraits :: Unlock

Spécialise un `CriticalSection` modèle afin qu’il prenne en charge la libération de la propriété de l’objet de section critique spécifié.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Paramètres

*cs*<br/>
Pointeur vers un objet de section critique.

### <a name="remarks"></a>Notes

Le `Type` modificateur est défini comme `typedef CRITICAL_SECTION* Type;` .

Pour plus d’informations, consultez **fonction LeaveCriticalSection** dans la section **fonctions de synchronisation** de la documentation de l’API Windows.
