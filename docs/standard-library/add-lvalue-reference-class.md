---
title: add_lvalue_reference, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_lvalue_reference
helpviewer_keywords:
- add_lvalue_reference
ms.assetid: 9933afc2-ad0d-465d-98fe-7d547fa3efe2
ms.openlocfilehash: 5f822e3393853c780bfe4ee86d5a5c799ec7646d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617675"
---
# <a name="add_lvalue_reference-class"></a>add_lvalue_reference, classe

Crée une référence vers un type à partir d'un type.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_lvalue_reference;

template <class T>
using add_lvalue_reference_t = typename add_lvalue_reference<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance du modificateur de type contient un type modifié qui est *t* si *t* est une référence lvalue, sinon `T&` .

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

using namespace std;
int main()
{
    int val = 0;
    add_lvalue_reference_t<int> p = (int&)val;
    p = p;  // to quiet "unused" warning
    cout << "add_lvalue_reference_t<int> == "
        << typeid(p).name() << endl;

    return (0);
}
```

```Output
add_lvalue_reference_t<int> == int
```

## <a name="requirements"></a>Configuration requise

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](type-traits.md)\
[Classe remove_reference](remove-reference-class.md)
