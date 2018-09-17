---
title: add_rvalue_reference, classe │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4936772c82bb482e468a37f2f7b327c9a728f0c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720120"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference, classe

Crée un type de référence rvalue du paramètre de modèle, s’il s’agit d’un type d’objet ou de fonction. Sinon, en raison de la sémantique de réduction de références, le type est le même que celui du paramètre de modèle.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à modifier.

## <a name="remarks"></a>Notes

Le `add_rvalue_reference` classe a un membre nommé `type`, qui est un alias pour le type d’une référence rvalue au paramètre de modèle *T*. La sémantique de réduction de références implique que, pour les types non-object et non-fonction *T*, `T&&` est un *T*. Par exemple, lorsque *T* est un type de référence lvalue, `add_rvalue_reference<T>::type` est le type de référence lvalue, pas une référence rvalue.

Pour des raisons pratiques, \<type_traits > définit un modèle d’assistance, `add_rvalue_reference_t`, cet alias le `type` membre de `add_rvalue_reference`.

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

En-tête : \<type_traits >

Namespace : std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_lvalue_reference, classe](../standard-library/add-lvalue-reference-class.md)<br/>
[is_rvalue_reference, classe](../standard-library/is-rvalue-reference-class.md)<br/>
