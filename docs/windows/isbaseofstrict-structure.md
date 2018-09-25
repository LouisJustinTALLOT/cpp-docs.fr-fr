---
title: IsBaseOfStrict (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
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
ms.openlocfilehash: 137f572f01d4aa72b9141c3ca172426fdb575b48
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169522"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename Base,
   typename Derived
>

struct IsBaseOfStrict;
template <
   typename Base
>
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
