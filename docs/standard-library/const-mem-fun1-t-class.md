---
title: const_mem_fun1_t, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32a748c240d8da55765ac5862c9a2f11eafb14ef
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201721"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t, classe

Classe d’adaptateur qui permet à une fonction membre **const** qui accepte un seul argument d’être appelée comme objet de fonction binaire en cas d’initialisation avec un argument de pointeur.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t
 : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* _Pm)(Arg) const);
    Result operator()(const Type* _Pleft, Arg right) const;
 };
```

### <a name="parameters"></a>Paramètres

*_Pm*<br/>
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*_Pleft*<br/>
Le **const** de l’objet qui le *_Pm* fonction membre est appelée sur.

*right*<br/>
L’argument donné à *_Pm*.

## <a name="return-value"></a>Valeur de retour

Fonction binaire adaptable.

## <a name="remarks"></a>Notes

La classe de modèle stocke une copie de *_Pm*, qui doit être un pointeur vers une fonction membre de classe `Type`, dans un objet de membre privé. Elle définit sa fonction membre `operator()` comme retournant ( *_Pleft*->\*<em>Pm</em>) ( *droit* ) **const**.

## <a name="example"></a>Exemple

Le constructeur de `const_mem_fun1_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun` est utilisée pour adapter les fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fun](../standard-library/functional-functions.md#mem_fun).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
