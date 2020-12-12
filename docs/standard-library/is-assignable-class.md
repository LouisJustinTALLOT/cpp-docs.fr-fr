---
description: 'En savoir plus sur : classe is_assignable'
title: is_assignable, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: 4165e69de99b7fdb8ae1524d1755e738c846d7c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323858"
---
# <a name="is_assignable-class"></a>is_assignable, classe

Teste si une valeur de type `From` peut être affectée à un type `To`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Paramètres

*À*\
Type de l'objet qui reçoit l'assignation.

*De*\
Type de l'objet qui fournit la valeur.

## <a name="remarks"></a>Notes

L’expression non évaluée `declval<To>() = declval<From>()` doit être bien formée. `From`Et doivent tous deux `To` être des types complets, **`void`** , ou des tableaux de limites inconnues.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
