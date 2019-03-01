---
title: const_mem_fun1_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: df984d90f8b632f8e3e3b183943343952d45b8be
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006355"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t, classe

Classe d’adaptateur qui permet à une fonction membre **const** qui accepte un seul argument d’être appelée comme objet de fonction binaire en cas d’initialisation avec un argument de pointeur. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* member_ptr)(Arg) const);
    Result operator()(const Type* left, Arg right) const;
};
```

### <a name="parameters"></a>Paramètres

*member_ptr*<br/>
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*left*<br/>
Le **const** de l’objet qui le *member_ptr* fonction membre est appelée sur.

*right*<br/>
L’argument donné à *member_ptr*.

## <a name="return-value"></a>Valeur de retour

Fonction binaire adaptable.

## <a name="remarks"></a>Notes

La classe de modèle stocke une copie de *member_ptr*, qui doit être un pointeur vers une fonction membre de classe `Type`, dans un objet de membre privé. Elle définit sa fonction membre `operator()` comme retournant `(left->member_ptr)(right) const`.

## <a name="example"></a>Exemple

Le constructeur de `const_mem_fun1_t` est rarement utilisé directement. `mem_fn` est utilisé pour adapter les fonctions membres. Consultez [mem_fn](../standard-library/functional-functions.md#mem_fn) pour obtenir un exemple montrant comment utiliser les adaptateurs de fonction membre.

## <a name="requirements"></a>Spécifications

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
