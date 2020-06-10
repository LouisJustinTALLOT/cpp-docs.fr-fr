---
title: add_rvalue_reference, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: 6d7cc1d45ed3b963de0a0a004c1696ddbf0af440
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623919"
---
# <a name="add_rvalue_reference-class"></a>add_rvalue_reference, classe

Crée un type de référence rvalue du paramètre de modèle, s’il s’agit d’un type d’objet ou de fonction. Sinon, en raison de la sémantique de réduction de références, le type est le même que celui du paramètre de modèle.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

La `add_rvalue_reference` classe a un membre nommé `type` , qui est un alias pour le type d’une référence rvalue au paramètre de modèle *T*. La sémantique de réduction de référence implique que, pour les types non-objet et non-fonction *t*, `T&&` est un *t*. Par exemple, quand *T* est un type de référence lvalue, `add_rvalue_reference<T>::type` est le type de référence lvalue, et non une référence rvalue.

Pour plus de commodité, \<type_traits> définit un modèle d’assistance, `add_rvalue_reference_t` , qui est l’alias du `type` membre de `add_rvalue_reference` .

## <a name="example"></a>Exemple

Cet exemple de code utilise static_assert pour montrer comment les types de référence rvalue sont créés à l’aide de `add_rvalue_reference` et `add_rvalue_reference_t`, et comment le résultat de `add_rvalue_reference` sur un type de référence lvalue n’est pas une référence rvalue, mais est réduit au type de référence lvalue.

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>Configuration requise

En-tête : \<type_traits>

Espace de noms : std

## <a name="see-also"></a>Voir aussi

[<type_traits>](type-traits.md)\
[Classe add_lvalue_reference](add-lvalue-reference-class.md)\
[Classe is_rvalue_reference](is-rvalue-reference-class.md)
