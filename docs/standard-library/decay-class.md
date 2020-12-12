---
description: 'En savoir plus sur : classe d’atténuation'
title: decay, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 6f6a1ebd31af44a48eaf400f9dccefdbd8ca3d01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324599"
---
# <a name="decay-class"></a>decay, classe

Génère le type comme passé par la valeur. Transforme un type en non-référence, non-const ou non-volatile, ou crée un pointeur vers le type à partir d’une fonction ou d’un type de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Utilisez le modèle de décomposition pour produire le type résultant comme si le type avait été passé comme argument par la valeur. Le typedef de membre de modèle de classe `type` contient un type modifié qui est défini au cours des étapes suivantes :

- Le type `U` est défini en tant que `remove_reference<T>::type`.

- Si `is_array<U>::value` a la valeur true, le type modifié `type` est `remove_extent<U>::type *`.

- Sinon, si `is_function<U>::value` a la valeur true, le type modifié `type` est `add_pointer<U>::type`.

- Sinon, le type modifié `type` est `remove_cv<U>::type`.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
