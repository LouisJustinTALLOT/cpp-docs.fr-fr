---
description: 'En savoir plus sur : classe result_of'
title: result_of, classe
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: 2aba6b073309be064b9ff0edc7bffa4d8d0098e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273902"
---
# <a name="result_of-class"></a>result_of, classe

Détermine le type de retour du type pouvant être appelé qui accepte les types d’argument spécifiés. Ajouté en C++ 14, déconseillé dans C++ 17.

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

*FN*\
Type pouvant être appelé à interroger.

*ArgTypes*\
Types de la liste d’arguments pour le type pouvant être appelé à interroger.

## <a name="remarks"></a>Notes

Utilisez ce modèle pour déterminer, au moment de la compilation, le type de résultat de `Fn` ( `ArgTypes` ), où *FN* est un type pouvant être appelé, une référence à une fonction ou une référence à un type pouvant être appelé, appelé à l’aide d’une liste d’arguments des types dans *argTypes*. Le `type` membre du modèle de classe nomme le type de résultat de `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` si l’expression non évaluée `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` est bien formée. Dans le cas contraire, le modèle de classe n’a aucun membre `type` . Le type *FN* et tous les types dans le jeu de paramètres *argTypes* doivent être des types complets, **`void`** , ou des tableaux de limites inconnues. Déconseillé en faveur de [invoke_result](invoke-result-class.md) en c++ 17.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[invoke_result, classe](invoke-result-class.md)
