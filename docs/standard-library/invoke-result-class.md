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
ms.openlocfilehash: 8cd72e62fcb65209482fd9677afcc2ec83356feb
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689520"
---
# <a name="invoke_result-class"></a>invoke_result, classe

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

@No__t_1 *pouvant être appelé*
Type pouvant être appelé à interroger.

*Arguments* \
Types de la liste d’arguments pour le type pouvant être appelé à interroger.

## <a name="remarks"></a>Notes

Utilisez ce modèle pour déterminer le type de résultat de *Callable*(*args*...) au moment de la compilation, où *Callable* et tous les types dans *args* sont tous des types complets, un tableau de limite inconnue ou un `void` potentiellement qualifié CV. Le `type` membre du modèle de classe nomme le type de retour *pouvant être appelé* lorsqu’il est appelé à l’aide des arguments *args*.... Le membre `type` est défini uniquement si *Callable* peut être appelé lors de l’appel à l’aide des arguments *args*... dans un contexte non évalué. Sinon, le modèle de classe n’a aucun membre `type`, qui autorise les tests SFINAE sur un jeu de types d’arguments particulier au moment de la compilation.

## <a name="requirements"></a>spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[déclenché](functional-functions.md#invoke)
