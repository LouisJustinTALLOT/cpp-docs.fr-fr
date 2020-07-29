---
title: HANDLENullTraits (structure)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
ms.openlocfilehash: a7ce730b8d723a839c5b509c825cff84111ca613
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226917"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits (structure)

Définit les caractéristiques communes d’un handle non initialisé.

## <a name="syntax"></a>Syntaxe

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | ---------------------
`Type` | Synonyme de descripteur.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                  | Description
----------------------------------------------------- | -----------------------------
[HANDLENullTraits :: Close](#close)                     | Ferme le handle spécifié.
[HANDLENullTraits :: Getinvalidvalue,](#getinvalidvalue) | Représente un handle non valide.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLENullTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers :: HandleTraits

## <a name="handlenulltraitsclose"></a><a name="close"></a>HANDLENullTraits :: Close

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

## <a name="handlenulltraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLENullTraits :: Getinvalidvalue,

Représente un handle non valide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours **`nullptr`** .
