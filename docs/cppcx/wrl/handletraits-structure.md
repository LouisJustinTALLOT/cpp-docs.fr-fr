---
description: 'En savoir plus sur : structure HANDLETraits'
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
ms.openlocfilehash: c3eef03c724b1ba868ba67ed251acdb310d8b66f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250021"
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

## <a name="handletraitsclose"></a><a name="close"></a> HANDLETraits :: Close

Ferme le handle spécifié.

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle à fermer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si handle *h* a été fermé avec succès ; Sinon, **`false`** .

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a> HANDLETraits :: Getinvalidvalue,

Représente un handle non valide.

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne toujours INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE est défini par Windows.)
