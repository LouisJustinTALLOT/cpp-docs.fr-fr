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
ms.openlocfilehash: cdec425e317585abbd9730447e2c4fbb19b8250a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784542"
---
# <a name="boolstruct-structure"></a>BoolStruct (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Notes

Le `BoolStruct` structure définit si un `ComPtr` gère la durée de vie d’une interface. `BoolStruct` est utilisé en interne par le [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype) opérateur.

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

Nom                          | Description
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct::Member](#member) | Spécifie qu’un [ComPtr](comptr-class.md) est ou n’est pas le cas, la gestion de la durée de vie d’une interface.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BoolStruct`

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="member"></a>BoolStruct::Member

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
int Member;
```

### <a name="remarks"></a>Notes

Spécifie qu’un [ComPtr](comptr-class.md) est ou n’est pas le cas, la gestion de la durée de vie d’une interface.
