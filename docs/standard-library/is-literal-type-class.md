---
title: is_literal_type, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_literal_type
dev_langs:
- C++
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a14b2fe5a14eaf264377a1f818227d73e134b030
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957961"
---
# <a name="isliteraltype-class"></a>is_literal_type, classe

Teste si un type peut être utilisé comme variable `constexpr`, ou être construit, utilisé par ou retourné à partir de fonctions `constexpr`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Paramètres

*T* type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un *type littéral*, sinon, sa valeur est false. Un type littéral est **void**, un type scalaire, un type référence, un tableau de type littéral ou un type de classe littéral. Un type de classe littéral est un type de classe qui a un destructeur trivial, est un type d’agrégation ou a au moins un constructeur `constexpr` sans déplacement et sans copie, et toutes ses classes de base et données membres non statiques sont des types littéraux non volatiles. Bien que le type d’un littéral soit toujours un type littéral, le concept de type littéral inclut tout ce que le compilateur peut évaluer en tant que `constexpr` au moment de la compilation.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
