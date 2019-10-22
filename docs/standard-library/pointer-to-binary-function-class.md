---
title: pointer_to_binary_function, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 890ebb7d4c2b8fbd51a4460e21efba3e763ead7e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687194"
---
# <a name="pointer_to_binary_function-class"></a>pointer_to_binary_function, classe

Convertit un pointeur de fonction binaire en fonction binaire adaptable. Déconseillé dans C++ 11, supprimé en C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>Paramètres

*pfunc* \
Fonction binaire à convertir.

\ *gauche*
Objet left sur lequel la fonction *\*pfunc* est appelée.

\ *droit*
Objet right sur lequel la fonction *\*pfunc* est appelée.

## <a name="return-value"></a>Valeur de retour

Le modèle de classe stocke une copie de `pfunc`. Elle définit sa fonction membre `operator()` comme retournant `(* pfunc)(Left, right)`.

## <a name="remarks"></a>Notes

Un pointeur de fonction binaire est un objet de fonction. Il peut être passé à n’importe quel algorithme de la bibliothèque standard C++ qui attend une fonction binaire comme paramètre, mais il n’est pas adaptable. Pour l’utiliser avec un adaptateur, par exemple la liaison d’une valeur à celui-ci ou son utilisation avec un inverse, il doit être fourni avec les types imbriqués `first_argument_type`, `second_argument_type` et `result_type` qui rendent cette adaptation possible. Grâce à la conversion par `pointer_to_binary_function`, les pointeurs de fonction binaire peuvent utiliser les adaptateurs de fonction.

## <a name="example"></a>Exemple

Le constructeur de `pointer_to_binary_function` est rarement utilisé directement. Consultez la fonction d’assistance [ptr_fun](../standard-library/functional-functions.md#ptr_fun) pour obtenir un exemple montrant comment déclarer et utiliser le prédicat de l’adaptateur `pointer_to_binary_function`.
