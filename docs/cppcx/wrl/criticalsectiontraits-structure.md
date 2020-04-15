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
ms.openlocfilehash: 05c93bf6a2765bd11489075067c627ab3c3ab691
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372580"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits (structure)

Il est `CriticalSection` spécialisé dans un objet à prendre en charge une section critique invalide ou une fonction de publication d’une section critique.

## <a name="syntax"></a>Syntaxe

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | Un `typedef` qui définit un pointeur à une section critique. `Type` est défini comme `typedef CRITICAL_SECTION* Type;`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                       | Description
---------------------------------------------------------- | -----------------
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | Se spécialise `CriticalSection` dans un modèle de sorte que le modèle est toujours invalide.
[CriticalSectionTraits::Unlock](#unlock)                   | Il est `CriticalSection` spécialisé dans un modèle qui prend en charge la libération de la propriété de l’objet de section critique spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CriticalSectionTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

Se spécialise `CriticalSection` dans un modèle de sorte que le modèle est toujours invalide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours un pointeur à une section critique invalide.

### <a name="remarks"></a>Notes

Le `Type` modificateur `typedef CRITICAL_SECTION* Type;`est défini comme .

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>CriticalSectionTraits::Unlock

Il est `CriticalSection` spécialisé dans un modèle qui prend en charge la libération de la propriété de l’objet de section critique spécifié.

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>Paramètres

*Cs*<br/>
Un pointeur vers un objet de section critique.

### <a name="remarks"></a>Notes

Le `Type` modificateur `typedef CRITICAL_SECTION* Type;`est défini comme .

Pour plus d’informations, consultez **la fonction LeaveCriticalSection** dans la section **Fonctions** de synchronisation de la documentation API Windows.
