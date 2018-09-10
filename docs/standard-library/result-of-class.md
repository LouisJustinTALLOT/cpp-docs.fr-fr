---
title: result_of, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
dev_langs:
- C++
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95ac984ad164c242dcd470ed4d31f3921fa7ec56
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103264"
---
# <a name="resultof-class"></a>result_of, classe

Détermine le type de retour du type pouvant être appelé qui accepte les types d’argument spécifiés.

## <a name="syntax"></a>Syntaxe

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>Paramètres

*fn*<br/>
Type pouvant être appelé à interroger.

*ArgTypes*<br/>
Types de la liste d’arguments pour le type pouvant être appelé à interroger.

## <a name="remarks"></a>Notes

Utilisez ce modèle pour déterminer au moment de la compilation le type de résultat de `Fn`(`ArgTypes`), où *Fn* est un type pouvant être appelé, référence à la fonction ou référence à un type pouvant être appelé, appelée à l’aide d’une liste des types d’arguments dans  *ArgTypes*. Le membre `type` de la classe de modèle désigne le type de résultat de `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` si l’expression non évaluée `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` est bien formée. Sinon, la classe de modèle n’a aucun membre `type`. Le type *Fn* et tous les types dans le pack de paramètre *ArgTypes* doivent être des types complets, **void**, ou des tableaux de limite inconnue.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
