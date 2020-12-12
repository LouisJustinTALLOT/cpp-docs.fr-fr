---
description: 'En savoir plus sur : classe is_literal_type'
title: is_literal_type, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 97cb609c5a42bed0be205b1b51ff901d3e366bb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323684"
---
# <a name="is_literal_type-class"></a>is_literal_type, classe

Teste si un type peut être utilisé comme **`constexpr`** variable ou être construit, utilisé par ou retourné à partir de **`constexpr`** fonctions.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un *type littéral*; sinon, sa valeur est false. Un type littéral est **`void`** , un type scalaire, un type référence, un tableau de type littéral ou un type de classe littérale. Un type de classe littérale est un type de classe qui a un destructeur trivial, est un type d’agrégation ou a au moins un constructeur non-déplacement, non-copie **`constexpr`** , et toutes ses classes de base et données membres non statiques sont des types de littéraux non volatils. Alors que le type d’un littéral est toujours un type littéral, le concept de type littéral comprend tout ce que le compilateur peut évaluer en tant que **`constexpr`** au moment de la compilation.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
