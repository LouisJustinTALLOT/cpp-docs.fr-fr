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
ms.openlocfilehash: b659f832756b79289181db34fa8d6fc0d974609d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610627"
---
# <a name="issame-structure"></a>IsSame (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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

*T2*<br/>
Un autre type.

## <a name="remarks"></a>Notes

Teste si un spécifié le type est identique à un autre de type spécifié.

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

Name                    | Description
----------------------- | --------------------------------------------------
[IsSame::value](#value) | Indique si un type est identique à un autre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IsSame`

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Namespace :** Microsoft::WRL::Details

## <a name="value"></a>IsSame::value

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

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

Indique si un type est identique à un autre.

`value` est **true** si les paramètres du modèle sont les mêmes, et **false** si les paramètres du modèle sont différents.
