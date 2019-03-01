---
title: pointer_to_binary_function, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_binary
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
ms.openlocfilehash: 88d38be258c6ceb1054e0d31cc52e4d8d25186ec
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006797"
---
# <a name="pointertobinaryfunction-class"></a>pointer_to_binary_function, classe

Convertit un pointeur de fonction binaire en fonction binaire adaptable. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
public:
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```

### <a name="parameters"></a>Paramètres

*pfunc*<br/>
Fonction binaire à convertir.

*left*<br/>
Objet left sur lequel la fonction *\*pfunc* est appelée.

*right*<br/>
Objet right sur lequel la fonction *\*pfunc* est appelée.

## <a name="return-value"></a>Valeur de retour

La classe de modèle stocke une copie de `pfunc`. Elle définit sa fonction membre `operator()` comme retournant `(* pfunc)(Left, right)`.

## <a name="remarks"></a>Notes

Un pointeur de fonction binaire est un objet de fonction. Il peut être passé à n’importe quel algorithme de la bibliothèque standard C++ qui attend une fonction binaire comme paramètre, mais il n’est pas adaptable. Pour l’utiliser avec un adaptateur, en le liant à une valeur ou l’utiliser avec une négation, vous devez également fournir les types imbriqués `first_argument_type`, `second_argument_type`, et `result_type` que rendre l’adaptation possible. Grâce à la conversion par `pointer_to_binary_function`, les pointeurs de fonction binaire peuvent utiliser les adaptateurs de fonction.

## <a name="example"></a>Exemple

Le constructeur de `pointer_to_binary_function` est rarement utilisé directement. Consultez la fonction d’assistance [ptr_fun](../standard-library/functional-functions.md#ptr_fun) pour obtenir un exemple montrant comment déclarer et utiliser le prédicat de l’adaptateur `pointer_to_binary_function`.

## <a name="requirements"></a>Spécifications

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
