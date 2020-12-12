---
description: 'En savoir plus sur : classe const_mem_fun1_t'
title: const_mem_fun1_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 998826bbd78745913caf76ad6b152aac490956fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233654"
---
# <a name="const_mem_fun1_t-class"></a>const_mem_fun1_t, classe

Classe d’adaptateur qui permet **`const`** à une fonction membre qui accepte un seul argument d’être appelée comme objet de fonction binaire en cas d’initialisation avec un argument de pointeur. Déconseillé dans C++ 11, supprimé en C++ 17.

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

*member_ptr*\
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*gauche*\
**`const`** Objet sur lequel la fonction membre *member_ptr* est appelée.

*Oui*\
Argument qui est donné à *member_ptr*.

## <a name="return-value"></a>Valeur renvoyée

Fonction binaire adaptable.

## <a name="remarks"></a>Notes

Le modèle de classe stocke une copie de *member_ptr*, qui doit être un pointeur vers une fonction membre de classe `Type` , dans un objet membre privé. Elle définit sa fonction membre `operator()` comme retournant `(left->member_ptr)(right) const` .

## <a name="example"></a>Exemple

Le constructeur de `const_mem_fun1_t` est rarement utilisé directement. `mem_fn` est utilisé pour adapter des fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fn](../standard-library/functional-functions.md#mem_fn) .
