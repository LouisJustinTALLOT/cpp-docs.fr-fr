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
ms.openlocfilehash: 4cbd3f367bc57c2eedf672422a458b67b1908fc0
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784438"
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
Un [RuntimeClassType (énumération)](runtimeclasstype-enumeration.md) valeur.

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|[RuntimeClassFlags::value, constante](#value-constant)|Contient un [RuntimeClassType (énumération)](runtimeclasstype-enumeration.md) valeur.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`RuntimeClassFlags`

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="value-constant"></a>Runtimeclassflags::value, constante

Un champ qui contient un [RuntimeClassType (énumération)](runtimeclasstype-enumeration.md) valeur.

```cpp
static const unsigned int value = flags;
```
