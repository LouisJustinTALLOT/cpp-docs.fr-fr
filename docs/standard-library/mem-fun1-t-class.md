---
title: mem_fun1_t, classe
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::mem_fun1_t
helpviewer_keywords:
- mem_fun1_t class
ms.assetid: 01a8c2c2-b2f7-4e3f-869c-5b5b9f06ea54
ms.openlocfilehash: 9a1fe26e66eb2ad20e6889b95640fadd2b3c45a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613193"
---
# <a name="memfun1t-class"></a>mem_fun1_t, classe

Classe d’adaptateur qui permet un `non_const` fonction membre qui accepte un seul argument d’être appelée comme objet de fonction binaire lors de l’initialisation avec un argument de pointeur.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_t : public binary_function<Type *, Arg, Result> {
    explicit mem_fun1_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type* _Pleft,
    Arg right) const;

};
```

### <a name="parameters"></a>Paramètres

*_Pm*<br/>
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*_Pleft*<br/>
L’objet qui le *_Pm* fonction membre est appelée sur.

*right*<br/>
L’argument donné à *_Pm*.

## <a name="return-value"></a>Valeur de retour

Fonction binaire adaptable.

## <a name="remarks"></a>Notes

La classe de modèle stocke une copie de *_Pm*, qui doit être un pointeur vers une fonction membre de classe `Type`, dans un objet de membre privé. Elle définit sa fonction membre `operator()` comme retournant ( **_Pleft**->\* `_Pm`)( **right**).

## <a name="example"></a>Exemple

Le constructeur de `mem_fun1_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun` est utilisée pour adapter les fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fun](../standard-library/functional-functions.md#mem_fun).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
