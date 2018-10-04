---
title: IsBaseOfStrict (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9fc41bdccf9cce3d455d4effd3541731929e5de2
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789265"
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

Le premier modèle teste si un type est dérivé d’un type de base, ce qui peut produire `true` ou `false`. Le deuxième modèle teste si un type est dérivé lui-même, ce qui génère toujours `false`.

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

`value` est `true` si type `Base` est une classe de base du type `Derived`, sinon il est `false`.
