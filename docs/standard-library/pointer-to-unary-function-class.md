---
description: 'En savoir plus sur : classe pointer_to_unary_function'
title: pointer_to_unary_function, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: 45a927add90915bcbd8791eeba5561027b7e9217
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340695"
---
# <a name="pointer_to_unary_function-class"></a>pointer_to_unary_function, classe

Convertit un pointeur de fonction unaire en fonction unaire adaptable. Déconseillé dans C++ 11, supprimé en C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Paramètres

*pFunc*\
Fonction binaire à convertir.

*gauche*\
Objet sur lequel le *\* pFunc* est appelé.

## <a name="return-value"></a>Valeur renvoyée

Le modèle de classe stocke une copie de `pfunc` . Elle définit sa fonction membre `operator()` comme retournant (\* **pfunc**)(_ *Left*).

## <a name="remarks"></a>Notes

Un pointeur de fonction unaire est un objet de fonction. Il peut être passé à n’importe quel algorithme de la bibliothèque standard C++ qui attend une fonction unaire comme paramètre, mais il n’est pas adaptable. Pour l’utiliser avec un adaptateur, tel que la liaison d’une valeur à celle-ci ou son utilisation avec un inverse, il doit être fourni avec les types imbriqués `argument_type` et `result_type` rendre une telle adaptation possible. Grâce à la conversion par `pointer_to_unary_function`, les pointeurs de fonction binaire peuvent utiliser les adaptateurs de fonction.

## <a name="example"></a>Exemple

Le constructeur de `pointer_to_unary_function` est rarement utilisé directement. Consultez la fonction d’assistance [ptr_fun](../standard-library/functional-functions.md#ptr_fun) pour obtenir un exemple montrant comment déclarer et utiliser le prédicat de l’adaptateur `pointer_to_unary_function`.
