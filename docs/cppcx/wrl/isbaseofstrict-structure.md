---
title: IsBaseOfStrict (structure)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: 71db5a1b52a7d7d5471c15591fb34d954b465d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371351"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict (structure)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Paramètres

*Base*<br/>
Type de base.

*Dérivé*<br/>
Le type dérivé.

## <a name="remarks"></a>Notes

Teste si un type est la base d'un autre.

Le premier modèle teste si un type est dérivé d’un type de base, ce qui peut donner **un rendement vrai** ou **faux**. Le deuxième modèle teste si un type est dérivé de lui-même, qui donne toujours **faux**.

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

Nom                            | Description
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::valeur](#value) | Indique si un type est la base d’un autre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IsBaseOfStrict`

## <a name="requirements"></a>Spécifications

**En-tête:** internal.h

**Espace nom:** Microsoft::WRL::Details

## <a name="isbaseofstrictvalue"></a><a name="value"></a>IsBaseOfStrict::valeur

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Notes

Indique si un type est la base d’un autre.

`value`est **vrai** `Base` si le type est `Derived`une classe de base du type , sinon il est **faux**.
