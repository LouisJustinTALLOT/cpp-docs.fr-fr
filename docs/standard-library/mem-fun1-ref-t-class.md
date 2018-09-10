---
title: mem_fun1_ref_t, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::mem_fun1_ref_t
dev_langs:
- C++
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b50f703dde69669c57e0f639e748ee596a3f1ab
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106585"
---
# <a name="memfun1reft-class"></a>mem_fun1_ref_t, classe

Classe d’adaptateur qui permet un `non_const` fonction membre qui accepte un seul argument d’être appelée comme objet de fonction binaire lors de l’initialisation avec un argument de référence.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type, class Arg>
class mem_fun1_ref_t : public binary_function<Type, Arg, Result> {
    explicit mem_fun1_ref_t(
    Result (Type::* _Pm)(Arg));

    Result operator()(
    Type& left,
    Arg right) const;

};
```

### <a name="parameters"></a>Paramètres

*_Pm*<br/>
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*left*<br/>
L’objet qui le *_Pm* fonction membre est appelée sur.

*right*<br/>
L’argument donné à *_Pm*.

## <a name="return-value"></a>Valeur de retour

Fonction binaire adaptable.

## <a name="remarks"></a>Notes

La classe de modèle stocke une copie de *_Pm*, qui doit être un pointeur vers une fonction membre de classe `Type`, dans un objet de membre privé. Elle définit sa fonction membre `operator()` comme retournant ( **gauche**.\* `_Pm`) ( **droit**).

## <a name="example"></a>Exemple

Le constructeur de `mem_fun1_ref_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun_ref` est utilisée pour adapter les fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
