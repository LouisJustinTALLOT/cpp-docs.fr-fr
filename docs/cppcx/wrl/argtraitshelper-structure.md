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
ms.openlocfilehash: fbba6d96106cc95910ccd9d0029cb3e9c254d7d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398834"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>Paramètres

*TDelegateInterface*<br/>
Une interface de délégué.

## <a name="remarks"></a>Notes

Permet de définir les caractéristiques communes d’arguments du délégué.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom         | Description
------------ | ------------------------------------------------------
`methodType` | Synonyme de `decltype(&TDelegateInterface::Invoke)`.
`Traits`     | Synonyme de `ArgTraits<methodType>`.

### <a name="public-constants"></a>Constantes publiques

Nom                           | Description
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper::args](#args) | Vous aide à [ArgTraits::args](#args) conserver le nombre de paramètres sur le `Invoke` méthode d’une interface de délégué.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ArgTraitsHelper`

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="args"></a>ArgTraitsHelper::args

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Notes

Vous aide à `ArgTraitsHelper::args` conserver le nombre de paramètres sur le `Invoke` méthode d’une interface de délégué.
