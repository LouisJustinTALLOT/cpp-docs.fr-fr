---
title: BoolStruct (structure)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
ms.openlocfilehash: 4f2a5acf6edb824cff2121c1b6444181b5cfcf98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371850"
---
# <a name="boolstruct-structure"></a>BoolStruct (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Notes

La `BoolStruct` structure définit `ComPtr` si a gère la durée de vie de l’objet d’une interface. `BoolStruct`est utilisé en interne par l’opérateur [BoolType.)](comptr-class.md#operator-microsoft-wrl-details-booltype)

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

Nom                          | Description
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct::Membre](#member) | Précise qu’un [ComPtr](comptr-class.md) gère ou non la durée de vie de l’objet d’une interface.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BoolStruct`

## <a name="requirements"></a>Spécifications

**En-tête:** internal.h

**Espace nom:** Microsoft::WRL::Details

## <a name="boolstructmember"></a><a name="member"></a>BoolStruct::Membre

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
int Member;
```

### <a name="remarks"></a>Notes

Précise qu’un [ComPtr](comptr-class.md) gère ou non la durée de vie de l’objet d’une interface.
