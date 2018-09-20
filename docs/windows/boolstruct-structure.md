---
title: BoolStruct (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
dev_langs:
- C++
helpviewer_keywords:
- BoolStruct structure
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13c1e57ec0b2f7459bdab447a6f7fe98ac8eb1d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416655"
---
# <a name="boolstruct-structure"></a>BoolStruct (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Notes

Le **BoolStruct** structure définit si un `ComPtr` gère la durée de vie d’une interface. **BoolStruct** est utilisé en interne par le [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) opérateur.

## <a name="members"></a>Membres

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[BoolStruct::Member, données de membre](../windows/boolstruct-member-data-member.md)|Spécifie qu’un [ComPtr](../windows/comptr-class.md) est ou n’est pas le cas, la gestion de la durée de vie d’une interface.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BoolStruct`

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)<br/>
[ComPtr::operator Microsoft::WRL::Details::BoolType, opérateur](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)