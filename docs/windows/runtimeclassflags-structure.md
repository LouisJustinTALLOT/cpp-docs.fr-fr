---
title: Runtimeclassflags, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClassFlags structure
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f0a32fc373900af1a4322f4f2511c44417d2916a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594272"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags (structure)

Contient le type d’une instance d’un [RuntimeClass](../windows/runtimeclass-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <
   unsigned int flags
>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Paramètres

*flags*  
Un [RuntimeClassType (énumération)](../windows/runtimeclasstype-enumeration.md) valeur.

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

|Name|Description|
|----------|-----------------|
|[RuntimeClassFlags::value, constante](../windows/runtimeclassflags-value-constant.md)|Contient un [RuntimeClassType (énumération)](../windows/runtimeclasstype-enumeration.md) valeur.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RuntimeClassFlags`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)