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
ms.openlocfilehash: 7c03240d3ee666fcda30562279a8dbda2ca8dc7b
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006870"
---
# <a name="invokeresult-class"></a>invoke_result, classe

Détermine le type de retour du type pouvant être appelé qui accepte les types d’arguments spécifiés au moment de la compilation. Ajouté dans C ++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<lass Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>Paramètres

*Callable*<br/>
Type pouvant être appelé à interroger.

*Args*<br/>
Types de la liste d’arguments pour le type pouvant être appelé à interroger.

## <a name="remarks"></a>Notes

Utilisez ce modèle pour déterminer le type de résultat de *joignable*(*Args*...) au moment de la compilation, où *joignable* et tous les types dans *Args* sont n’importe quel type terminée, un tableau de limite inconnue ou un éventuellement cv-qualifié `void`. Le `type` membre de la classe de modèle désigne le type de retour de *joignable* lorsqu’elle est appelée à l’aide des arguments *Args*... Le `type` membre est défini uniquement si *joignable* peut être appelée lorsqu’elle est appelée à l’aide des arguments *Args*... dans un contexte non évalué. Sinon, la classe de modèle n’a aucun membre `type`, ce qui permet de SFINAE des tests sur un ensemble particulier de types d’argument au moment de la compilation.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)
