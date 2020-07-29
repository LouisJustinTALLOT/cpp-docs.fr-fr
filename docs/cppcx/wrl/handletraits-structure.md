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
ms.openlocfilehash: c04e53789fd737b12ca10ef2c279a05fb43f5925
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212993"
---
# <a name="handletraits-structure"></a>HANDLETraits (structure)

Définit les caractéristiques communes d’un handle.

## <a name="syntax"></a>Syntaxe

```cpp
struct HANDLETraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | ---------------------
`Type` | Synonyme de descripteur.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                              | Description
------------------------------------------------- | -----------------------------
[HANDLETraits :: Close](#close)                     | Ferme le handle spécifié.
[HANDLETraits :: Getinvalidvalue,](#getinvalidvalue) | Représente un handle non valide.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLETraits`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers :: HandleTraits

## <a name="handletraitsclose"></a><a name="close"></a>HANDLETraits :: Close

Ferme le handle spécifié.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle à fermer.

### <a name="return-value"></a>Valeur de retour

**`true`** Si handle *h* a été fermé avec succès ; Sinon, **`false`** .

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLETraits :: Getinvalidvalue,

Représente un handle non valide.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE est défini par Windows.)
