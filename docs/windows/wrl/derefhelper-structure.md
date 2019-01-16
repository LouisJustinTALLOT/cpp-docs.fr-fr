---
title: DerefHelper (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 7709ae63e4d49e25aec83a069ad1ac614bfbd953
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335952"
---
# <a name="derefhelper-structure"></a>DerefHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un paramètre de modèle.

## <a name="remarks"></a>Notes

Représenter un pointeur déréférencé au `T*` paramètre de modèle.

**DerefHelper** est utilisé dans une expression comme : `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`DerefType`|Identificateur pour le paramètre de modèle déréférencé `T*`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DerefHelper`

## <a name="requirements"></a>Spécifications

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)