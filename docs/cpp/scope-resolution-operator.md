---
title: 'Opérateur de résolution de portée : `::`'
description: Découvrez comment fonctionne l’opérateur `::` de résolution de portée en C++ standard.
ms.date: 12/06/2020
f1_keywords:
- '::'
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.openlocfilehash: ff774d9fcca9f68cb2925af82c55ef438ab4d71a
ms.sourcegitcommit: 7b131db4ed39bddb4a456ebea402f47c5cbd69d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96776529"
---
# <a name="scope-resolution-operator-"></a>Opérateur de résolution de portée : `::`

L’opérateur de résolution de portée **`::`** est utilisé pour identifier et lever l’ambiguïté des identificateurs utilisés dans différentes portées. Pour plus d’informations sur l’étendue, consultez [scope](../cpp/scope-visual-cpp.md).

## <a name="syntax"></a>Syntaxe

> *`qualified-id`*:\
> &emsp;*`nested-name-specifier`***`template`** <sub>OPT</sub>*`unqualified-id`*

> *`nested-name-specifier`*:\
> &emsp;**`::`**\
> &emsp;*`type-name`* **`::`**\
> &emsp;*`namespace-name`* **`::`**\
> &emsp;*`decltype-specifier`* **`::`**\
> &emsp;*`nested-name-specifier`* *`identifier`* **`::`**\
> &emsp;*`nested-name-specifier`***`template`** <sub>opt</sub> opt *`simple-template-id`***`::`**

> *`unqualified-id`*:\
> &emsp;*`identifier`*\
> &emsp;*`operator-function-id`*\
> &emsp;*`conversion-function-id`*\
> &emsp;*`literal-operator-id`*\
> &emsp;**`~`** *`type-name`*\
> &emsp;**`~`** *`decltype-specifier`*\
> &emsp;*`template-id`*

## <a name="remarks"></a>Remarques

`identifier` peut être une variable, une fonction ou une valeur d'énumération.

## <a name="use--for-classes-and-namespaces"></a>`::`À utiliser pour les classes et les espaces de noms

L’exemple suivant montre comment l’opérateur de résolution de portée est utilisé avec les espaces de noms et les classes :

```cpp
namespace NamespaceA{
    int x;
    class ClassA {
    public:
        int x;
    };
}

int main() {

    // A namespace name used to disambiguate
    NamespaceA::x = 1;

    // A class name used to disambiguate
    NamespaceA::ClassA a1;
    a1.x = 2;
}
```

Un opérateur de résolution de portée sans qualificateur de portée fait référence à l'espace de noms global.

```cpp
namespace NamespaceA{
    int x;
}

int x;

int main() {
    int x;

    // the x in main()
    x = 0;
    // The x in the global namespace
    ::x = 1;

    // The x in the A namespace
    NamespaceA::x = 2;
}
```

Vous pouvez utiliser l’opérateur de résolution de portée pour identifier un membre d’un **`namespace`** ou pour identifier un espace de noms qui désigne l’espace de noms du membre dans une **`using`** directive. Dans l’exemple ci-dessous, vous pouvez utiliser `NamespaceC` pour qualifier `ClassB` , même si `ClassB` a été déclaré dans l’espace de noms `NamespaceB` , car `NamespaceB` a été désigné `NamespaceC` par une **`using`** directive.

```cpp
namespace NamespaceB {
    class ClassB {
    public:
        int x;
    };
}

namespace NamespaceC{
    using namespace NamespaceB;
}

int main() {
    NamespaceB::ClassB b_b;
    NamespaceC::ClassB c_b;

    b_b.x = 3;
    c_b.x = 4;
}
```

Vous pouvez utiliser des chaînes d'opérateurs de résolution de portée. Dans l'exemple suivant, `NamespaceD::NamespaceD1` identifie l'espace de noms imbriqué `NamespaceD1` et `NamespaceE::ClassE::ClassE1` identifie la classe imbriquée `ClassE1`.

```cpp
namespace NamespaceD{
    namespace NamespaceD1{
        int x;
    }
}

namespace NamespaceE{
    class ClassE{
    public:
        class ClassE1{
        public:
            int x;
        };
    };
}

int main() {
    NamespaceD:: NamespaceD1::x = 6;
    NamespaceE::ClassE::ClassE1 e1;
    e1.x = 7  ;
}
```

## <a name="use--for-static-members"></a>`::`À utiliser pour les membres statiques

Vous devez utiliser l'opérateur de résolution de portée pour appeler des membres statiques de classes.

```cpp
class ClassG {
public:
    static int get_x() { return x;}
    static int x;
};

int ClassG::x = 6;

int main() {

    int gx1 = ClassG::x;
    int gx2 = ClassG::get_x();
}
```

## <a name="use--for-scoped-enumerations"></a>Utiliser `::` pour les énumérations délimitées

L’opérateur de résolution de portée est également utilisé avec les valeurs des [déclarations d’énumération](../cpp/enumerations-cpp.md)d’énumération délimitées, comme dans l’exemple suivant :

```cpp
enum class EnumA{
    First,
    Second,
    Third
};

int main() {
    EnumA enum_value = EnumA::First;
}
```

## <a name="see-also"></a>Voir aussi

[Opérateurs, priorité et associativité C++ intégrés](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Espaces de noms](../cpp/namespaces-cpp.md)
