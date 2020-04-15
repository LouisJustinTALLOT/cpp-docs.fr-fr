---
title: HANDLETraits (structure)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
ms.openlocfilehash: 604098cd3289722767117910d6e44e272dcb8b77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371448"
---
# <a name="handletraits-structure"></a>HANDLETraits (structure)

Définit les caractéristiques communes d’une poignée.

## <a name="syntax"></a>Syntaxe

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | ---------------------
`Type` | Un synonyme de HANDLE.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                              | Description
------------------------------------------------- | -----------------------------
[HANDLETraits::Fermer](#close)                     | Ferme la poignée spécifiée.
[HANDLETraits::GetInvalidValue](#getinvalidvalue) | Représente une poignée invalide.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLETraits`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="handletraitsclose"></a><a name="close"></a>HANDLETraits::Fermer

Ferme la poignée spécifiée.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Le manche à fermer.

### <a name="return-value"></a>Valeur de retour

**vrai** si poignée *h* fermé avec succès; autrement, **faux**.

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLETraits::GetInvalidValue

Représente une poignée invalide.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE est définie par Windows.)
