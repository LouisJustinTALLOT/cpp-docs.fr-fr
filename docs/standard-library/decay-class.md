---
title: decay, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 3b22dfecb1162ce67a0d648197465115acb044ba
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688116"
---
# <a name="decay-class"></a>decay, classe

Produit le type passé par la valeur. Transforme un type en non-référence, non-const ou non-volatile, ou crée un pointeur vers le type à partir d’une fonction ou d’un type de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>Paramètres

*T* \
Type à modifier.

## <a name="remarks"></a>Notes

Utilisez le modèle de décomposition pour produire le type résultant comme si le type avait été passé comme argument par la valeur. Le `type` de membre de modèle de classe TypeDef contient un type modifié qui est défini aux étapes suivantes :

- Le type `U` est défini en tant que `remove_reference<T>::type`.

- Si `is_array<U>::value` a la valeur true, le type modifié `type` est `remove_extent<U>::type *`.

- Sinon, si `is_function<U>::value` a la valeur true, le type modifié `type` est `add_pointer<U>::type`.

- Sinon, le type modifié `type` est `remove_cv<U>::type`.

## <a name="requirements"></a>spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
