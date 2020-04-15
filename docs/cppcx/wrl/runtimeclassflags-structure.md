---
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
ms.openlocfilehash: 9fed5bb31b077288495a78aefcbd8401b3520bb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367223"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags (structure)

Contient le type par exemple d’une [RuntimeClass](runtimeclass-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>Paramètres

*Drapeaux*<br/>
Une valeur [d’énumération RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[RuntimeClassFlags::value, constante](#value-constant)|Contient une valeur [d’énumération RuntimeClassType.](runtimeclasstype-enumeration.md)|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RuntimeClassFlags`

## <a name="requirements"></a>Spécifications

**En-tête:** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="runtimeclassflagsvalue-constant"></a><a name="value-constant"></a>RuntimeClassFlags::valeur Constante

Un champ qui contient une valeur [d’énumération RuntimeClassType.](runtimeclasstype-enumeration.md)

```cpp
static const unsigned int value = flags;
```
