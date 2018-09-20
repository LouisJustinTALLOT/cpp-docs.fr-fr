---
title: Makeallocator::Detach, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3ef07b3de2125c38064bc2a0f15559e8ef6084d4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443382"
---
# <a name="makeallocatordetach-method"></a>MakeAllocator::Detach, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline void Detach();
```

## <a name="remarks"></a>Notes

Dissocie la mémoire allouée par le [Allocate](../windows/makeallocator-allocate-method.md) (méthode) à partir du **MakeAllocator** objet.

Si vous appelez **Detach()**, vous êtes responsable de la suppression de la mémoire fournie par le `Allocate` (méthode).

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[MakeAllocator, classe](../windows/makeallocator-class.md)<br/>
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)