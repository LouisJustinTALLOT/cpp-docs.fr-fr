---
title: pointer_to_unary_function, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: 710453711e60f4607a20eb3e71b65127c8dd5316
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006654"
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function, classe

Convertit un pointeur de fonction unaire en fonction unaire adaptable. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
public:
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Paramètres

*pfunc*<br/>
Fonction binaire à convertir.

*left*<br/>
Objet sur lequel la fonction *\*pfunc* est appelée.

## <a name="return-value"></a>Valeur de retour

La classe de modèle stocke une copie de `pfunc`. Elle définit sa fonction membre `operator()` comme retournant (\* **pfunc**)(_ *Left*).

## <a name="remarks"></a>Notes

Un pointeur de fonction unaire est un objet de fonction. Il peut être passé à n’importe quel algorithme de la bibliothèque standard C++ qui attend une fonction unaire comme paramètre, mais il n’est pas adaptable. Pour l’utiliser avec un adaptateur, en le liant à une valeur ou l’utiliser avec une négation, vous devez également fournir les types imbriqués `argument_type` et `result_type` que rendre l’adaptation possible. Grâce à la conversion par `pointer_to_unary_function`, les pointeurs de fonction binaire peuvent utiliser les adaptateurs de fonction.

## <a name="example"></a>Exemple

Le constructeur de `pointer_to_unary_function` est rarement utilisé directement. Consultez la fonction d’assistance [ptr_fun](../standard-library/functional-functions.md#ptr_fun) pour obtenir un exemple montrant comment déclarer et utiliser le prédicat de l’adaptateur `pointer_to_unary_function`.

## <a name="requirements"></a>Spécifications

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
