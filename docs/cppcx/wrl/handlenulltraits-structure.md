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
ms.openlocfilehash: d70425f414b998eb67e3937c2c126dd3eda0c00d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398379"
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
`Type` | Synonyme de HANDLE.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                  | Description
----------------------------------------------------- | -----------------------------
[HANDLENullTraits::Close](#close)                     | Ferme le handle spécifié.
[HANDLENullTraits::GetInvalidValue](#getinvalidvalue) | Représente un handle non valide.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLENullTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>HANDLENullTraits::Close

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

## <a name="getinvalidvalue"></a>HANDLENullTraits::GetInvalidValue

Représente un handle non valide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours `nullptr`.
