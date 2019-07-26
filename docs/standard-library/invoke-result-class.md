---
title: invoke_result, classe
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: 2b2051b0c854151cff9b439f5ec0a951c25a6387
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447640"
---
# <a name="invokeresult-class"></a>invoke_result, classe

Détermine le type de retour du type pouvant être appelé qui accepte les types d’arguments spécifiés au moment de la compilation. Ajouté en C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Paramètres

*Pouvant être appelé*\
Type pouvant être appelé à interroger.

*Attend*\
Types de la liste d’arguments pour le type pouvant être appelé à interroger.

## <a name="remarks"></a>Notes

Utilisez ce modèle pour déterminer le type de résultat de Callable (*args*...) au moment de la compilation, où les types *pouvant être appelés* et tous les types dans *args* sont tous des types complets, un tableau de limites `void`inconnues ou une valeur de CV potentiellement qualifiée. Le `type` membre de la classe de modèle nomme le type de retour *pouvant être appelé* lorsqu’il est appelé à l’aide des arguments *args*.... Le `type` membre est défini uniquement si *Callable* peut être appelé lorsqu’il est appelé à l’aide des arguments *args*... dans un contexte non évalué. Sinon, la classe de modèle n’a `type`aucun membre, ce qui permet aux tests SFINAE sur un jeu particulier de types d’arguments au moment de la compilation.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
