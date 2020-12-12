---
description: 'En savoir plus sur : structure Derefhelper ('
title: DerefHelper (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 8605e3923d8d3099a080be22f9d8e70ee9187ef9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272914"
---
# <a name="derefhelper-structure"></a>DerefHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Paramètre de modèle.

## <a name="remarks"></a>Notes

Représente un pointeur déréférencé vers le `T*` paramètre de modèle.

**Derefhelper (** est utilisé dans une expression telle que : `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;` .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`DerefType`|Identificateur du paramètre de modèle déréférencé `T*` .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DerefHelper`

## <a name="requirements"></a>Spécifications

**En-tête :** Async. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL ::D espace de noms étails](microsoft-wrl-details-namespace.md)
