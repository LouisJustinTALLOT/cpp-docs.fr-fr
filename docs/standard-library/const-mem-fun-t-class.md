---
description: 'En savoir plus sur : classe const_mem_fun_t'
title: const_mem_fun_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: cfde3048758673b1918e3cc8eaab7151dde59896
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233667"
---
# <a name="const_mem_fun_t-class"></a>const_mem_fun_t, classe

Classe d’adaptateur qui permet à une fonction membre const qui n’accepte aucun argument d’être appelée comme objet de fonction unaire en cas d’initialisation avec un argument de référence. Déconseillé dans C++ 11, supprimé en C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
};
```

### <a name="parameters"></a>Paramètres

*Manuel*\
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*Pleft*\
Objet sur lequel la fonction membre *PM* est appelée.

## <a name="return-value"></a>Valeur renvoyée

Fonction unaire adaptable.

## <a name="remarks"></a>Notes

Le modèle de classe stocke une copie de *PM*, qui doit être un pointeur vers une fonction membre de classe `Type` , dans un objet membre privé. Elle définit sa fonction membre `operator()` comme retournant ( `Pleft` -> \* `Pm` ) () **`const`** .

## <a name="example"></a>Exemple

Le constructeur de `const_mem_fun_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun` est utilisée pour adapter les fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fun](../standard-library/functional-functions.md#mem_fun).
