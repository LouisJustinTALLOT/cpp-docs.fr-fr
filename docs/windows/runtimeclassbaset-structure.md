---
title: Runtimeclassbaset, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
dev_langs:
- C++
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b0bae186a0c4d4e9a6c7eec8553c296428b3a59
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597189"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT, structure

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   unsigned int RuntimeClassTypeT
>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Paramètres

*RuntimeClassTypeT*  
Un champ d’indicateurs qui spécifie un ou plusieurs [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) énumérateurs.

## <a name="remarks"></a>Notes

Fournit des méthodes d’assistance pour `QueryInterface` opérations et l’obtention des ID d’interface.

## <a name="members"></a>Membres

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RuntimeClassBaseT`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Référence (Windows Runtime Library)](http://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)