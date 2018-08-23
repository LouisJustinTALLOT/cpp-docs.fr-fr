---
title: Interfacetraits::Verify, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: 46edd67f-7952-4552-a157-55e823f616c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c6491968541a0015110c55edf2bede40c084947
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583442"
---
# <a name="interfacetraitsverify-method"></a>InterfaceTraits::Verify, méthode

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline static void Verify();
```

## <a name="remarks"></a>Notes

Vérifie que `Base` est dérivé correctement.

Pour plus d’informations sur `Base`, consultez le **Typedefs publics** section [InterfaceTraits (Structure)](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[InterfaceTraits, structure](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)