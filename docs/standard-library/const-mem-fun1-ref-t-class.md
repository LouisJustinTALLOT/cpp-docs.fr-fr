---
title: const_mem_fun1_ref_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun1_ref_t
helpviewer_keywords:
- const_mem_fun1_ref_t class
ms.assetid: 8220d373-fa1c-44be-a21d-96d49b3ea6bb
ms.openlocfilehash: 76fae1ce29cb4c47870e45e8f946f6ff1fea1885
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688174"
---
# <a name="const_mem_fun1_ref_t-class"></a>const_mem_fun1_ref_t, classe

Classe d’adaptateur qui permet à une fonction membre **const** qui accepte un seul argument d’être appelée comme objet de fonction binaire en cas d’initialisation avec un argument de référence. Déconseillé dans C++ 11, supprimé en C++ 17.

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

@No__t_1 *PM*
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

\ *gauche*
Objet **const** sur lequel la fonction membre *PM* est appelée.

\ *droit*
Argument qui est donné à *PM*.

## <a name="return-value"></a>Valeur de retour

Fonction binaire adaptable.

## <a name="remarks"></a>Notes

Le modèle de classe stocke une copie de *PM*, qui doit être un pointeur vers une fonction membre de la classe `Type`, dans un objet membre privé. Elle définit sa fonction membre `operator()` comme retournant (`left`. \* *PM*) (`right`) **const**.

## <a name="example"></a>Exemple

Le constructeur de `const_mem_fun1_ref_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun_ref` est utilisée pour adapter les fonctions membres. Pour obtenir des exemples d’utilisation des adaptateurs de fonction membre, consultez [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).
