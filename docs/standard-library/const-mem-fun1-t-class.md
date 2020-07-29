---
title: const_mem_fun1_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_t
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
ms.openlocfilehash: 93d0e7a116c7c7ba7a2ed1cb46fd88585a99120d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228321"
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

## <a name="return-value"></a>Valeur de retour

Fonction binaire adaptable.

## <a name="remarks"></a>Notes

Le modèle de classe stocke une copie de *member_ptr*, qui doit être un pointeur vers une fonction membre de classe `Type` , dans un objet membre privé. Elle définit sa fonction membre `operator()` comme retournant `(left->member_ptr)(right) const` .

## <a name="example"></a>Exemple

Le constructeur de `const_mem_fun1_t` est rarement utilisé directement. `mem_fn`est utilisé pour adapter des fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fn](../standard-library/functional-functions.md#mem_fn) .
