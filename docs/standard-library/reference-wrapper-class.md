---
title: reference_wrapper, classe
ms.date: 11/04/2016
f1_keywords:
- functional/std::reference_wrapper
- type_traits/std::reference_wrapper
- xrefwrap/std::reference_wrapper
- type_traits/std::reference_wrapper::get
- type_traits/std::reference_wrapper::operator()
- functional/std::reference_wrapper::result_type
- functional/std::reference_wrapper::type
- functional/std::reference_wrapper::get
- functional/std::reference_wrapper::operator()
helpviewer_keywords:
- std::reference_wrapper [C++]
- std::reference_wrapper [C++]
- std::reference_wrapper [C++], result_type
- std::reference_wrapper [C++], type
- std::reference_wrapper [C++], get
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
ms.openlocfilehash: 623e1480bdec85120e504c8dc71b28d017c8872a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845066"
---
# <a name="reference_wrapper-class"></a>reference_wrapper, classe

Encapsule une référence.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class reference_wrapper
{
    typedef Ty type;

    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types>
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));
};
```

## <a name="remarks"></a>Notes

Un `reference_wrapper<Ty>` est un wrapper constructible par copie et assignable par copie autour d’une référence à un objet ou une fonction de type `Ty`. Il contient un pointeur vers un objet de ce type. Un `reference_wrapper` peut être utilisé pour stocker des références dans des conteneurs standard et passer des objets par référence à `std::bind`.

Le type `Ty` doit être un type d’objet ou un type de fonction. Sinon, une assertion statique échoue au moment de la compilation.

Les fonctions d’assistance [std::ref](functional-functions.md#ref) et [std::cref](functional-functions.md#cref) peuvent être utilisées pour créer des objets `reference_wrapper`.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|-|-|
|[reference_wrapper](#reference_wrapper)|Construit un objet `reference_wrapper`.|

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|-|-|
|[result_type](#result_type)|Type de résultat faible de la référence encapsulée.|
|[type](#type)|Type de la référence encapsulée.|

### <a name="functions"></a>Functions

|Nom|Description|
|-|-|
|[get](#get)|Obtient la référence encapsulée.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[Ty, opérateur&amp;](#op_ty_amp)|Obtient un pointeur vers la référence encapsulée.|
|[, opérateur ()](#op_call)|Appelle la référence encapsulée.|

## <a name="get"></a><a name="get"></a> Télécharger

Obtient la référence encapsulée.

```cpp
Ty& get() const noexcept;
```

### <a name="remarks"></a>Notes

La fonction membre retourne la référence incluse dans un wrapper.

### <a name="example"></a>Exemple

```cpp
// std__functional__reference_wrapper_get.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="operator-tyamp"></a><a name="op_ty_amp"></a> Ty, opérateur&amp;

Obtient la référence incluse dans un wrapper.

```cpp
operator Ty&() const noexcept;
```

### <a name="remarks"></a>Notes

L’opérateur membre retourne `*ptr`.

### <a name="example"></a>Exemple

```cpp
// std__functional__reference_wrapper_operator_cast.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "(int)rwi = " << (int)rwi << std::endl;

    return (0);
}
```

```Output
i = 1
(int)rwi = 1
```

## <a name="operator"></a><a name="op_call"></a> , opérateur ()

Appelle la référence encapsulée.

```cpp
template <class... Types>
auto operator()(Types&&... args);
```

### <a name="parameters"></a>Paramètres

*Modes*\
Types de la liste d’arguments.

*attend*\
Liste d’arguments.

### <a name="remarks"></a>Notes

Le membre de modèle `operator()` retourne `std::invoke(get(), std::forward<Types>(args)...)`.

### <a name="example"></a>Exemple

```cpp
// std__functional__reference_wrapper_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    std::reference_wrapper<int (int)> rwi(neg);

    std::cout << "rwi(3) = " << rwi(3) << std::endl;

    return (0);
}
```

```Output
rwi(3) = -3
```

## <a name="reference_wrapper"></a><a name="reference_wrapper"></a> reference_wrapper

Construit un objet `reference_wrapper`.

```cpp
reference_wrapper(Ty& val) noexcept;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à inclure dans un wrapper.

*multiples*\
Valeur à inclure dans un wrapper.

### <a name="remarks"></a>Notes

Le constructeur définit la valeur stockée `ptr` à `&val`.

### <a name="example"></a>Exemple

```cpp
// std__functional__reference_wrapper_reference_wrapper.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    std::reference_wrapper<int> rwi(i);

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << rwi << std::endl;
    rwi.get() = -1;
    std::cout << "i = " << i << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
i = -1
```

## <a name="result_type"></a><a name="result_type"></a> result_type

Type de résultat faible de la référence encapsulée.

```cpp
typedef R result_type;
```

### <a name="remarks"></a>Notes

Le typedef `result_type` est un synonyme pour le type de résultat faible d’une fonction incluse dans un wrapper. Ce typedef est significatif uniquement pour les types de fonction.

### <a name="example"></a>Exemple

```cpp
// std__functional__reference_wrapper_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    typedef std::reference_wrapper<int (int)> Mywrapper;
    Mywrapper rwi(neg);
    Mywrapper::result_type val = rwi(3);

    std::cout << "val = " << val << std::endl;

    return (0);
}
```

```Output
val = -3
```

## <a name="type"></a>Type<a name="type"></a>

Type de la référence encapsulée.

```cpp
typedef Ty type;
```

### <a name="remarks"></a>Notes

Le typedef est un synonyme de l'argument de modèle `Ty`.

### <a name="example"></a>Exemple

```cpp
// std__functional__reference_wrapper_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val) {
    return (-val);
}

int main() {
    int i = 1;
    typedef std::reference_wrapper<int> Mywrapper;
    Mywrapper rwi(i);
    Mywrapper::type val = rwi.get();

    std::cout << "i = " << i << std::endl;
    std::cout << "rwi = " << val << std::endl;

    return (0);
}
```

```Output
i = 1
rwi = 1
```
