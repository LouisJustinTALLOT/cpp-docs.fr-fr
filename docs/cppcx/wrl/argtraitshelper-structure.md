---
description: 'En savoir plus sur : structure ArgTraitsHelper'
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
ms.openlocfilehash: a749c48c72c837eb0898d32ddd08410b87918871
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175857"
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
Interface de délégué.

## <a name="remarks"></a>Notes

Permet de définir les caractéristiques communes des arguments de délégué.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom         | Description
------------ | ------------------------------------------------------
`methodType` | Synonyme de `decltype(&TDelegateInterface::Invoke)`.
`Traits`     | Synonyme de `ArgTraits<methodType>`.

### <a name="public-constants"></a>Constantes publiques

Nom                           | Description
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[ArgTraitsHelper :: args](#args) | Aide [ArgTraits :: args](#args) à conserver le nombre de paramètres sur la `Invoke` méthode d’une interface de délégué.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ArgTraitsHelper`

## <a name="requirements"></a>Spécifications

**En-tête :** Event. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="argtraitshelperargs"></a><a name="args"></a> ArgTraitsHelper :: args

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Notes

Permet de `ArgTraitsHelper::args` conserver le nombre de paramètres sur la `Invoke` méthode d’une interface de délégué.
