---
description: 'En savoir plus sur : classe pointer_to_binary_function'
title: pointer_to_binary_function, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 5cdecc297ff5c55c9b6c57b5b6ab029636f3958c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340708"
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

*pFunc*\
Fonction binaire à convertir.

*gauche*\
Objet de gauche sur lequel le *\* pFunc* est appelé.

*Oui*\
Objet de droite sur lequel le *\* pFunc* est appelé.

## <a name="return-value"></a>Valeur renvoyée

Le modèle de classe stocke une copie de `pfunc` . Elle définit sa fonction membre `operator()` comme retournant `(* pfunc)(Left, right)` .

## <a name="remarks"></a>Notes

Un pointeur de fonction binaire est un objet de fonction. Il peut être passé à n’importe quel algorithme de la bibliothèque standard C++ qui attend une fonction binaire comme paramètre, mais il n’est pas adaptable. Pour l’utiliser avec un adaptateur, par exemple la liaison d’une valeur à celui-ci ou son utilisation avec un inverse, il doit être fourni avec les types imbriqués `first_argument_type` , `second_argument_type` et `result_type` qui rend une telle adaptation possible. Grâce à la conversion par `pointer_to_binary_function`, les pointeurs de fonction binaire peuvent utiliser les adaptateurs de fonction.

## <a name="example"></a>Exemple

Le constructeur de `pointer_to_binary_function` est rarement utilisé directement. Consultez la fonction d’assistance [ptr_fun](../standard-library/functional-functions.md#ptr_fun) pour obtenir un exemple montrant comment déclarer et utiliser le prédicat de l’adaptateur `pointer_to_binary_function`.
