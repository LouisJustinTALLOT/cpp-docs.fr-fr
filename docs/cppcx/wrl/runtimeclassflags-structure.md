---
description: 'En savoir plus sur : structure RuntimeClassFlags'
title: RuntimeClassFlags (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 7874447fbbbe429884c5a79d0c70bb93e617ec61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209267"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags (structure)

Contient le type d’une instance d’un [RuntimeClass](runtimeclass-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Paramètres

*flags*<br/>
Valeur d' [énumération RuntimeClassType](runtimeclasstype-enumeration.md) .

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[RuntimeClassFlags::value, constante](#value-constant)|Contient une valeur d' [énumération RuntimeClassType](runtimeclasstype-enumeration.md) .|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RuntimeClassFlags`

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="runtimeclassflagsvalue-constant"></a><a name="value-constant"></a> RuntimeClassFlags :: value, constante

Champ qui contient une valeur d' [énumération RuntimeClassType](runtimeclasstype-enumeration.md) .

```cpp
static const unsigned int value = flags;
```
