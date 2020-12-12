---
description: 'En savoir plus sur : structure IsBaseOfStrict'
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
ms.openlocfilehash: bcdab9c4b6b5a2ab108b59d3127c08b53589e16a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298953"
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
Type dérivé.

## <a name="remarks"></a>Notes

Teste si un type est la base d'un autre.

Le premier modèle teste si un type est dérivé d’un type de base, ce qui peut générer **`true`** ou **`false`** . Le deuxième modèle teste si un type est dérivé de lui-même, ce qui produit toujours **`false`** .

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

Nom                            | Description
------------------------------- | --------------------------------------------------
[IsBaseOfStrict :: value](#value) | Indique si un type est la base d’un autre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IsBaseOfStrict`

## <a name="requirements"></a>Spécifications

**En-tête :** Internal. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="isbaseofstrictvalue"></a><a name="value"></a> IsBaseOfStrict :: value

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Notes

Indique si un type est la base d’un autre.

`value` est **`true`** si `Base` le type est une classe de base du type ; `Derived` sinon, il s’agit de **`false`** .
