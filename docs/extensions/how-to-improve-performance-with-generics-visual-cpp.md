---
title: Guide pratique pour améliorer les performances avec des génériques (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: 039c5b069351249e51d961d9d1757ed6b09ef99c
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414163"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>Guide pratique pour améliorer les performances avec des génériques (C++/CLI)

Avec les génériques, vous pouvez créer du code réutilisable basé sur un paramètre de type. Le type réel du paramètre de type est différé jusqu’à ce qu’il soit appelé par le code client. Pour plus d’informations sur les types génériques, consultez [Generics](generics-cpp-component-extensions.md).

Cet article explique comment les génériques permettent d’augmenter les performances d’une application qui utilise des collections.

## <a name="example-two-main-drawbacks-of-net-framework-collections"></a>Exemple : deux inconvénients principaux des regroupements de .NET Framework

.NET Framework est livré avec de nombreuses classes de collection dans l’espace de noms <xref:System.Collections?displayProperty=fullName>. La plupart de ces collections fonctionnent sur des objets de type <xref:System.Object?displayProperty=fullName>. Ainsi, les collections peuvent stocker tous les types, étant donné que tous les types dans le .NET Framework, y compris les types valeur, dérivent de <xref:System.Object?displayProperty=fullName>. Cependant, il existe deux inconvénients à cette approche.

Tout d’abord, si la collection stocke des types valeur tels que des entiers, la valeur doit être convertie (boxed) avant d’être ajoutée à la collection et unboxed quand la valeur est récupérée à partir de la collection. Ces opérations sont coûteuses.

Ensuite, il n’existe aucun moyen de contrôler les types à ajouter à une collection. Il est parfaitement légal d’ajouter un entier et une chaîne à la même collection, même si cela n’est pas ce qui était prévu. Par conséquent, afin que votre code soit de type sécurisé, vous devez vérifier que le type récupéré à partir de la collection est vraiment le type attendu.

L’exemple de code suivant montre les deux principaux inconvénients des collections .NET Framework antérieures aux génériques.

```cpp
// perf_pre_generics.cpp
// compile with: /clr

using namespace System;
using namespace System::Collections;

int main()
{
    // This Stack can contain any type.
    Stack ^s = gcnew Stack();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);

    // Push a String to the same Stack.
    // The Stack now contains two different data types.
    s->Push("Seven");

    // Pop the items off the Stack.
    // The item is returned as an Object, so a cast is
    // necessary to convert it to its proper type.
    while (s->Count> 0)
    {
        Object ^o = s->Pop();
        if (o->GetType() == Type::GetType("System.String"))
        {
            Console::WriteLine("Popped a String: {0}", (String ^)o);
        }
        else if (o->GetType() == Type::GetType("System.Int32"))
        {
            Console::WriteLine("Popped an int: {0}", (int)o);
        }
        else
        {
            Console::WriteLine("Popped an unknown type!");
        }
    }
}
```

```Output
Popped a String: Seven
Popped an int: 7
```

## <a name="example-benefit-of-using-generic-collection"></a>Exemple : avantage de l’utilisation de la collection générique

Le nouvel espace de noms <xref:System.Collections.Generic?displayProperty=fullName> contient la plupart des collections qui se trouvent dans l’espace de noms <xref:System.Collections?displayProperty=fullName>, mais celles-ci ont été modifiées pour accepter les paramètres de type générique. Cela permet d’éliminer les deux inconvénients des collections non génériques : la conversion boxing et unboxing des types valeur et l’incapacité de spécifier les types à stocker dans les collections. Les opérations sur les deux collections sont identiques ; elles diffèrent uniquement dans la façon dont elles sont instanciées.

Comparez l’exemple présenté ci-dessus avec cet exemple qui utilise une collection <xref:System.Collections.Generic.Stack%601> générique. Les performances de cet exemple seront bien plus importantes sur les grandes collections auxquelles vous accédez souvent que pour l’exemple précédent.

```cpp
// perf_post_generics.cpp
// compile with: /clr

#using <System.dll>

using namespace System;
using namespace System::Collections::Generic;

int main()
{
    // This Stack can only contain integers.
    Stack<int> ^s = gcnew Stack<int>();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);
    s->Push(14);

    // You can no longer push a String to the same Stack.
    // This will result in compile time error C2664.
    //s->Push("Seven");

    // Pop an item off the Stack.
    // The item is returned as the type of the collection, so no
    // casting is necessary and no unboxing is performed for
    // value types.
    int i = s->Pop();
    Console::WriteLine(i);

    // You can no longer retrieve a String from the Stack.
    // This will result in compile time error C2440.
    //String ^str = s->Pop();
}
```

```Output
14
```

## <a name="see-also"></a>Voir aussi

[Génériques](generics-cpp-component-extensions.md)
