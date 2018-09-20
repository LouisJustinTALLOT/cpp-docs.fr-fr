---
title: DontUseNewUseMake (classe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
dev_langs:
- C++
helpviewer_keywords:
- DontUseNewUseMake class
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc2b2f03cfbd488de8358b2e4b123716efcbfe15
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431305"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake (classe)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Notes

Empêche l’utilisation d’opérateur **nouveau** dans `RuntimeClass`. Par conséquent, vous devez utiliser le [Make, fonction](../windows/make-function.md) à la place.

## <a name="members"></a>Membres

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[DontUseNewUseMake::operator new, opérateur](../windows/dontusenewusemake-operator-new-operator.md)|Surcharge d’opérateur **nouveau** et empêche l’utilisation dans `RuntimeClass`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DontUseNewUseMake`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)<br/>
[Make, fonction](../windows/make-function.md)