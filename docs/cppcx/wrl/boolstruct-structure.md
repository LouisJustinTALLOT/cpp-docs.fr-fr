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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865706"
---
# <a name="boolstruct-structure"></a>BoolStruct (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Notes

La structure `BoolStruct` définit si une `ComPtr` gère la durée de vie des objets d’une interface. `BoolStruct` est utilisé en interne par l’opérateur [booltype, ()](comptr-class.md#operator-microsoft-wrl-details-booltype) .

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publiques

Name                          | Description
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct :: Member](#member) | Spécifie qu’un [ComPtr](comptr-class.md) est ou qu’il gère la durée de vie des objets d’une interface.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BoolStruct`

## <a name="requirements"></a>Spécifications

**En-tête :** Internal. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="member"></a>BoolStruct :: Member

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
int Member;
```

### <a name="remarks"></a>Notes

Spécifie qu’un [ComPtr](comptr-class.md) est ou qu’il gère la durée de vie des objets d’une interface.
