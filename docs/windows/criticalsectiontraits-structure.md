---
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
ms.openlocfilehash: ce904ecbd9a5855c63fd43f07f88c215cef544ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451088"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits (structure)

Spécialise une `CriticalSection` objet pour prendre en charge une section critique non valide ou une fonction d’annulation d’une section critique.

## <a name="syntax"></a>Syntaxe

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | Un `typedef` qui définit un pointeur vers une section critique. `Type` est défini en tant que `typedef CRITICAL_SECTION* Type;`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                       | Description
---------------------------------------------------------- | -----------------
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | Spécialise une `CriticalSection` modèle afin que le modèle est toujours non valide.
[CriticalSectionTraits::Unlock](#unlock)                   | Spécialise une `CriticalSection` modèle afin qu’il prend en charge la libération de la propriété de l’objet de section critique spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CriticalSectionTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

Spécialise une `CriticalSection` modèle afin que le modèle est toujours non valide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours un pointeur vers une section critique non valide.

### <a name="remarks"></a>Notes

Le `Type` modificateur est défini comme `typedef CRITICAL_SECTION* Type;`.

## <a name="unlock"></a>CriticalSectionTraits::Unlock

Spécialise une `CriticalSection` modèle afin qu’il prend en charge la libération de la propriété de l’objet de section critique spécifié.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Paramètres

*cs*<br/>
Pointeur vers un objet de section critique.

### <a name="remarks"></a>Notes

Le `Type` modificateur est défini comme `typedef CRITICAL_SECTION* Type;`.

Pour plus d’informations, consultez **LeaveCriticalSection fonction** dans le **des fonctions de synchronisation** section de la documentation de l’API de Windows.
