---
title: Classe invoke_result
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: e3e1a28310660ad1fbdae4dd58973de378ddf364
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233130"
---
# <a name="invoke_result-class"></a>Classe invoke_result

Détermine le type de retour du type pouvant être appelé qui accepte les types d’arguments spécifiés au moment de la compilation. Ajouté en C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<class Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Paramètres

*Pouvant être appelé*\
Type pouvant être appelé à interroger.

*Attend*\
Types de la liste d’arguments pour le type pouvant être appelé à interroger.

## <a name="remarks"></a>Notes

Utilisez ce modèle pour déterminer le type de résultat de *Callable*(*args*...) au moment de la compilation, où les types *pouvant être appelés* et tous les types dans *args* sont tous des types complets, un tableau de limites inconnues ou une valeur de CV potentiellement qualifiée **`void`** . Le `type` membre du modèle de classe nomme le type de retour *pouvant être appelé* lorsqu’il est appelé à l’aide des arguments *args*.... Le `type` membre est défini uniquement si *Callable* peut être appelé lorsqu’il est appelé à l’aide des arguments *args*... dans un contexte non évalué. Sinon, le modèle de classe n’a aucun membre `type` , ce qui permet aux tests SFINAE sur un jeu de types d’arguments particulier au moment de la compilation.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
