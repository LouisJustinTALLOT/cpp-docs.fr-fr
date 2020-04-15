---
title: ArgTraitsHelper (structure)
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
ms.openlocfilehash: 4acbd9fa660f29bbaf209282ff0e90f43621574d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360772"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Paramètres

*TDelegateInterface*<br/>
Une interface déléguée.

## <a name="remarks"></a>Notes

Aide à définir les caractéristiques communes des arguments des délégués.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom         | Description
------------ | ------------------------------------------------------
`methodType` | Synonyme de `decltype(&TDelegateInterface::Invoke)`.
`Traits`     | Synonyme de `ArgTraits<methodType>`.

### <a name="public-constants"></a>Constantes publiques

Nom                           | Description
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | Aide [ArgTraits::args](#args) garder le compte du `Invoke` nombre de paramètres sur la méthode d’une interface déléguée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ArgTraitsHelper`

## <a name="requirements"></a>Spécifications

**En-tête:** event.h

**Espace nom:** Microsoft::WRL::Details

## <a name="argtraitshelperargs"></a><a name="args"></a>ArgTraitsHelper::args

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Notes

Permet `ArgTraitsHelper::args` de garder le compte du `Invoke` nombre de paramètres sur la méthode d’une interface déléguée.
