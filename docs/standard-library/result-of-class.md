---
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
ms.openlocfilehash: f60a3ef6528da33fd1117fc940e961e9fe0987df
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006550"
---
# <a name="resultof-class"></a>result_of, classe

Détermine le type de retour du type pouvant être appelé qui accepte les types d’argument spécifiés. Ajouté dans C ++ 14, déconseillées dans C ++ 17.

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

*Fn*<br/>
Type pouvant être appelé à interroger.

*ArgTypes*<br/>
Types de la liste d’arguments pour le type pouvant être appelé à interroger.

## <a name="remarks"></a>Notes

Utilisez ce modèle pour déterminer au moment de la compilation le type de résultat de `Fn`(`ArgTypes`), où *Fn* est un type pouvant être appelé, référence à la fonction ou référence à un type pouvant être appelé, appelée à l’aide d’une liste des types d’arguments dans  *ArgTypes*. Le membre `type` de la classe de modèle désigne le type de résultat de `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` si l’expression non évaluée `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` est bien formée. Sinon, la classe de modèle n’a aucun membre `type`. Le type *Fn* et tous les types dans le pack de paramètre *ArgTypes* doivent être des types complets, **void**, ou des tableaux de limite inconnue. Déconseillé en faveur de [invoke_result](invoke-result-class.md) dans C ++ 17.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[classe d’invoke_result](invoke-result-class.md)<br/>
