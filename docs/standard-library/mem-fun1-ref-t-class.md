---
description: 'En savoir plus sur : classe mem_fun1_ref_t'
title: mem_fun1_ref_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun1_ref_t
helpviewer_keywords:
- mem_fun1_ref_t class
ms.assetid: 7d6742f6-19ba-4523-b3c8-0e5b8f11464f
ms.openlocfilehash: 6418812fb4c924c8d67ba4fc09d4595455ad73c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149121"
---
# <a name="mem_fun1_ref_t-class"></a>mem_fun1_ref_t, classe

Classe d’adaptateur qui permet `non_const` à une fonction membre qui accepte un seul argument d’être appelée comme objet de fonction binaire en cas d’initialisation avec un argument de référence. Déconseillé dans C++ 11, supprimé en C++ 17.

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

*_Pm*\
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*gauche*\
Objet sur lequel la fonction membre *_Pm* est appelée.

*Oui*\
Argument qui est donné à *_Pm*.

## <a name="return-value"></a>Valeur renvoyée

Fonction binaire adaptable.

## <a name="remarks"></a>Notes

Le modèle de classe stocke une copie de *_Pm*, qui doit être un pointeur vers une fonction membre de classe `Type` , dans un objet membre privé. Elle définit sa fonction membre `operator()` comme retournant (**Left**. \* `_Pm` ) (à **droite**).

## <a name="example"></a>Exemple

Le constructeur de `mem_fun1_ref_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun_ref` est utilisée pour adapter les fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).
