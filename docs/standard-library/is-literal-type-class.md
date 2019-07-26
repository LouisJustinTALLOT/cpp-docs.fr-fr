---
title: is_literal_type, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 450c32d050a18f64e71992bd7a30412ebafe93de
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456215"
---
# <a name="isliteraltype-class"></a>is_literal_type, classe

Teste si un type peut être utilisé comme variable `constexpr`, ou être construit, utilisé par ou retourné à partir de fonctions `constexpr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un *type littéral*; sinon, sa valeur est false. Un type littéral est **void**, un type scalaire, un type référence, un tableau de type littéral ou un type de classe littérale. Un type de classe littéral est un type de classe qui a un destructeur trivial, est un type d’agrégation ou a au moins un constructeur `constexpr` sans déplacement et sans copie, et toutes ses classes de base et données membres non statiques sont des types littéraux non volatiles. Bien que le type d’un littéral soit toujours un type littéral, le concept de type littéral inclut tout ce que le compilateur peut évaluer en tant que `constexpr` au moment de la compilation.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
