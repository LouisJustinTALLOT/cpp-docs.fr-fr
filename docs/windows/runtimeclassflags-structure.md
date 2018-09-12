---
title: Runtimeclassflags, Structure | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6c3cb141576598aa39c718316048900622c4df41
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691456"
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
|[RuntimeClassFlags::value, constante](#value-constant)|Contient un [RuntimeClassType (énumération)](../windows/runtimeclasstype-enumeration.md) valeur.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RuntimeClassFlags`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="value-constant"></a>Runtimeclassflags::value, constante

Un champ qui contient un [RuntimeClassType (énumération)](../windows/runtimeclasstype-enumeration.md) valeur.
  
```cpp
static const unsigned int value = flags;
```
