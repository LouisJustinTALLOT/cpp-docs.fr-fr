---
title: HANDLENullTraits (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1060d28e35a52e2a8c5c550664d36d8272628526
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161734"
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

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

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
