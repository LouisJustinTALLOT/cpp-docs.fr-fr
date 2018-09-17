---
title: is_assignable, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 339b3cdb2e2470fea976ef8257e6a84f089d3dd9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712554"
---
# <a name="isassignable-class"></a>is_assignable, classe

Teste si une valeur de type `From` peut être affectée à un type `To`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Paramètres

*To*<br/>
Type de l'objet qui reçoit l'assignation.

*From*<br/>
Type de l'objet qui fournit la valeur.

## <a name="remarks"></a>Notes

L’expression non évaluée `declval<To>() = declval<From>()` doit être bien formée. Les deux `From` et `To` doivent être des types complets, **void**, ou des tableaux de limite inconnue.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
