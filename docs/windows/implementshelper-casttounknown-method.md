---
title: Implementshelper::casttounknown, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: 5bcfcbaf-c75f-4d43-87b3-0d6838c838d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc36793eba9f2500020795ef9e88e63663d350c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402160"
---
# <a name="implementshelpercasttounknown-method"></a>ImplementsHelper::CastToUnknown, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
IUnknown* CastToUnknown();
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet sous-jacent `IUnknown` interface.

## <a name="remarks"></a>Notes

Obtient un pointeur vers sous-jacent `IUnknown` interface actif `Implements` structure.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[ImplementsHelper, structure](../windows/implementshelper-structure.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)