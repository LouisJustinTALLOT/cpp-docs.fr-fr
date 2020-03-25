---
title: Cibles d’attribut (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
ms.openlocfilehash: fe2c1d27042b51300d01ba70b951b7601d87701e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172618"
---
# <a name="attribute-targets-ccli-and-ccx"></a>Cibles d’attribut (C++/CLI et C++/CX)

Les spécificateurs de l’utilisation d’attributs permettent de spécifier les cibles d’attribut.  Chaque attribut est défini pour s’appliquer à certains éléments de langage. Par exemple, un attribut peut être défini pour s’appliquer uniquement aux classes et aux structs.  La liste suivante montre les éléments syntaxiques possibles sur lesquels un attribut personnalisé peut être utilisé. Vous pouvez utiliser des combinaisons de ces valeurs (à l’aide de l’opérateur logique OR).

Pour spécifier la cible d’attribut, pour passer un ou plusieurs énumérateurs <xref:System.AttributeTargets> à <xref:System.AttributeUsageAttribute> lors de la définition de l’attribut.

Voici une liste des cibles d’attribut valide :

- `All` (s’applique à toutes les constructions)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::All)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Assembly` (s’applique à un assembly dans son ensemble)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Assembly)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Module` (s’applique à un module dans son ensemble)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Module)]
    ref class Attr : public Attribute {};

    [module:Attr];
    ```

- `Class`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Class)]
    ref class Attr : public System::Attribute {};

    [Attr]   // same as [class:Attr]
    ref class MyClass {};
    ```

- `Struct`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Struct)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [struct:Attr]
    value struct MyStruct{};
    ```

- `enum`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Enum)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [enum:Attr]
    enum struct MyEnum{e, d};
    ```

- `Constructor`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Constructor)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] MyStruct(){}   // same as [constructor:Attr]
    };
    ```

- `Method`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Method)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] void Test(){}   // same as [method:Attr]
    };
    ```

- `Property`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Property)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] property int Test;   // same as [property:Attr]
    };
    ```

- `Field`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Field)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] int Test;   // same as [field:Attr]
    };
    ```

- `Event`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Event)]
    ref class Attr : public Attribute {};

    delegate void ClickEventHandler(int, double);

    ref struct MyStruct{
    [Attr] event ClickEventHandler^ OnClick;   // same as [event:Attr]
    };
    ```

- `Interface`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Interface)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [event:Attr]
    interface struct MyStruct{};
    ```

- `Parameter`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Parameter)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    void Test([Attr] int i);
    void Test2([parameter:Attr] int i);
    };
    ```

- `Delegate`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Delegate)]
    ref class Attr : public Attribute {};

    [Attr] delegate void Test();
    [delegate:Attr] delegate void Test2();
    ```

- `ReturnValue`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::ReturnValue)]
    ref class Attr : public Attribute {};

    ref struct MyStruct {
    // Note required specifier
    [returnvalue:Attr] int Test() { return 0; }
    };
    ```

En règle générale, un attribut précède directement l’élément de langage auquel il s’applique. Toutefois, dans certains cas, la position d’un attribut n’est pas suffisante pour déterminer la cible prévue de l’attribut. Examinez cet exemple :

```cpp
[Attr] int MyFn(double x)...
```

D’un point de vue syntaxique, il n’existe aucun moyen de savoir si l’attribut doit s’appliquer à la méthode ou à la valeur de retour de la méthode (dans ce cas, il s’applique par défaut à la méthode). Dans ce cas, vous pouvez utiliser un spécificateur d’utilisation de l’attribut. Par exemple, pour appliquer l’attribut à la valeur de retour, utilisez le spécificateur `returnvalue`, comme suit :

```cpp
[returnvalue:Attr] int MyFn(double x)... // applies to return value
```

Des spécificateurs d’utilisation d’attribut sont requis dans les situations suivantes :

- Pour spécifier un attribut de niveau assembly ou module.

- Pour spécifier qu’un attribut s’applique à la valeur de retour d’une méthode, et non pas la méthode :

    ```cpp
    [method:Attr] int MyFn(double x)...     // Attr applies to method
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value
    [Attr] int MyFn(double x)...            // default: method
    ```

- Pour spécifier qu’un attribut s’applique à l’accesseur d’une propriété, et non pas la propriété :

    ```cpp
    [method:MyAttr(123)] property int Property()
    [property:MyAttr(123)] property int Property()
    [MyAttr(123)] property int get_MyPropy() // default: property
    ```

- Pour spécifier qu’un attribut s’applique à l’accesseur d’un événement, et non pas l’événement :

    ```cpp
    delegate void MyDel();
    ref struct X {
       [field:MyAttr(123)] event MyDel* MyEvent;   //field
       [event:MyAttr(123)] event MyDel* MyEvent;   //event
       [MyAttr(123)] event MyDel* MyEvent;   // default: event
    }
    ```

Un spécificateur d’utilisation de l’attribut s’applique uniquement à l’attribut qui le suit immédiatement ; c’est-à-dire,

```cpp
[returnvalue:Attr1, Attr2]
```

est différent de

```cpp
[returnvalue:Attr1, returnvalue:Attr2]
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Cet exemple montre comment spécifier plusieurs cibles.

### <a name="code"></a>Code

```cpp
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Struct, AllowMultiple = true )]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};

[Attr]
[Attr(true)]
value struct MyStruct {};
```

## <a name="see-also"></a>Voir aussi

[Attributs définis par l'utilisateur](user-defined-attributes-cpp-component-extensions.md)
