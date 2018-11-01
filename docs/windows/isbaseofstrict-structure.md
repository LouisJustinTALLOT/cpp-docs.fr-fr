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
ms.openlocfilehash: 85aeb71ceaa162cc6366836dd286f2f9983d34e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506156"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Paramètres

*base de*<br/>
Type de base.

*DÉRIVÉS*<br/>
Le type dérivé.

## <a name="remarks"></a>Notes

Teste si un type est la base d'un autre.

Le premier modèle teste si un type est dérivé d’un type de base, ce qui peut produire **true** ou **false**. Le deuxième modèle teste si un type est dérivé lui-même, ce qui entraîne toujours une valeur **false**.

## <a name="members"></a>Membres

### <a name="public-constants"></a>Constantes publiques

Name                            | Description
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::value](#value) | Indique si un type est la base d’un autre.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IsBaseOfStrict`

## <a name="requirements"></a>Configuration requise

**En-tête :** internal.h

**Namespace :** Microsoft::WRL::Details

## <a name="value"></a>IsBaseOfStrict::value

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Notes

Indique si un type est la base d’un autre.

`value` est **true** si type `Base` est une classe de base du type `Derived`, sinon il est **false**.
