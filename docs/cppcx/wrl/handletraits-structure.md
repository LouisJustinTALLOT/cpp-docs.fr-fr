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
ms.openlocfilehash: 4dd2cde62d36c46926e703e6fb649e2ae4ef7811
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784515"
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
`Type` | Synonyme de HANDLE.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                              | Description
------------------------------------------------- | -----------------------------
[HANDLETraits::Close](#close)                     | Ferme le handle spécifié.
[HANDLETraits::GetInvalidValue](#getinvalidvalue) | Représente un handle non valide.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLETraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>HANDLETraits::Close

Ferme le handle spécifié.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Le handle à fermer.

### <a name="return-value"></a>Valeur de retour

**true** si gérer *h* fermé avec succès ; sinon, **false**.

## <a name="getinvalidvalue"></a>HANDLETraits::GetInvalidValue

Représente un handle non valide.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE est défini par Windows.)
