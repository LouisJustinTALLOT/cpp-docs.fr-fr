---
title: const_mem_fun1_ref_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 21d53178bf7ed80b5e0b170619e6221826393dab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212012"
---
# <a name="constmemfun1reft-class"></a>const_mem_fun1_ref_t, classe

Classe d’adaptateur qui permet à une fonction membre **const** qui accepte un seul argument d’être appelée comme objet de fonction binaire en cas d’initialisation avec un argument de référence. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_ref_t
: public binary_function<Type, Arg, Result>
{
    explicit const_mem_fun1_ref_t(Result (Type::* Pm)(Arg) const);
    Result operator()(const Type& left, Arg right) const;
};
```

### <a name="parameters"></a>Paramètres

*Pm*<br/>
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*left*<br/>
Le **const** de l’objet qui le *Pm* fonction membre est appelée sur.

*right*<br/>
L’argument donné à *Pm*.

## <a name="return-value"></a>Valeur de retour

Fonction binaire adaptable.

## <a name="remarks"></a>Notes

La classe de modèle stocke une copie de *Pm*, qui doit être un pointeur vers une fonction membre de classe `Type`, dans un objet de membre privé. Elle définit sa fonction membre `operator()` comme retournant ( `left`.\* *Pm*)( `right`) **const**.

## <a name="example"></a>Exemple

Le constructeur de `const_mem_fun1_ref_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun_ref` est utilisée pour adapter les fonctions membres. Pour obtenir des exemples d’utilisation des adaptateurs de fonction membre, consultez [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
