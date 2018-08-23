---
title: Issame::value, constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: ee72deff-54a2-4482-9967-49a86d07f834
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 299ee0f1c2a892a3219c2337e01d629eadec8a82
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42580992"
---
# <a name="issamevalue-constant"></a>IsSame::value, constante

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

## <a name="remarks"></a>Notes

Indique si un type est identique à un autre.

**valeur** est **true** si les paramètres du modèle sont les mêmes, et **false** si les paramètres du modèle sont différents.

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[IsSame, structure](../windows/issame-structure.md)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)