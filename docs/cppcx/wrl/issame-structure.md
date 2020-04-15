---
title: IsSame (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
ms.openlocfilehash: fcaf33309521b44163022e0ffa9b1e03e53e2551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371347"
---
# <a name="issame-structure"></a>IsSame (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>Paramètres

*T1*<br/>
Type.

*T2 T2*<br/>
Un autre type.

## <a name="remarks"></a>Notes

Teste si un type spécifié est le même qu’un autre type spécifié.

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

Nom                    | Description
----------------------- | --------------------------------------------------
[IsSame::valeur](#value) | Indique si un type est le même qu’un autre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IsSame`

## <a name="requirements"></a>Spécifications

**En-tête:** internal.h

**Espace nom:** Microsoft::WRL::Details

## <a name="issamevalue"></a><a name="value"></a>IsSame::valeur

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

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

### <a name="remarks"></a>Notes

Indique si un type est le même qu’un autre.

`value`est **vrai** si les paramètres du modèle sont les mêmes, et **faux** si les paramètres du modèle sont différents.
