---
title: Implements::casttounknown, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 988580a34c030c84c50adfff2741408be4b249cd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586356"
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown, méthode

Obtient un pointeur vers sous-jacent `IUnknown` interface.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline IUnknown* CastToUnknown();
```

## <a name="return-value"></a>Valeur de retour

Cette opération réussit et retourne toujours le `IUnknown` pointeur.

## <a name="remarks"></a>Notes

Fonction d’assistance interne.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Implements, structure](../windows/implements-structure.md)