---
title: 'Comment : améliorer les performances avec des génériques (C++ / c++ / CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ead9491e7b5302cadfa59eb7d98215fb3c41eb09
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327817"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>Comment : améliorer les performances avec des génériques (C++ / c++ / CLI)

Avec les génériques, vous pouvez créer du code réutilisable basé sur un paramètre de type. Le type réel du paramètre de type est différé jusqu'à ce qu’appelé par le code client. Pour plus d’informations sur les types génériques, consultez [Generics](../windows/generics-cpp-component-extensions.md).

Cet article explique comment les génériques permettent d’augmenter les performances d’une application qui utilise des regroupements.

## <a name="example"></a>Exemple

Le .NET Framework est livré avec de nombreuses classes de collection dans le <xref:System.Collections?displayProperty=fullName> espace de noms. La plupart de ces collections opèrent sur des objets de type <xref:System.Object?displayProperty=fullName>. Ainsi, les collections pour stocker n’importe quel type, étant donné que tous les types dans le .NET Framework, même les types valeur dérivent <xref:System.Object?displayProperty=fullName>. Toutefois, il existe deux inconvénients à cette approche.

Tout d’abord, si la collection stocke des types de valeur tels que les entiers, la valeur doit être converti (boxed) avant d’être ajouté à la collection et unboxed quand la valeur est récupérée à partir de la collection. Il s’agit des opérations coûteuses.

Deuxièmement, il n’existe aucun moyen pour contrôler les types peuvent être ajoutés à une collection. Il est parfaitement possible d’ajouter un entier et une chaîne à la même collection, même si cela est probablement pas ce qui a été prévu. Par conséquent, afin que votre code doit être de type sécurisé, vous devez vérifier que le type récupéré à partir de la collection est vraiment ce qui était attendu.

L’exemple de code suivant montre les deux principaux inconvénients des collections .NET Framework antérieure aux génériques.

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

## <a name="example"></a>Exemple

La nouvelle <xref:System.Collections.Generic?displayProperty=fullName> espace de noms contient un grand nombre de la même collection trouvée dans le <xref:System.Collections?displayProperty=fullName> espace de noms, mais ils ont été modifiés pour accepter les paramètres de type générique. Cela permet d’éliminer les deux inconvénients de collections non génériques : la conversion boxing et unboxing de types valeur et l’impossibilité pour spécifier les types à stocker dans les collections. Opérations sur les deux collections sont identiques ; elles diffèrent uniquement dans la façon dont ils sont instanciés.

Comparez l’exemple suivant écrit ci-dessus avec cet exemple qui utilise un générique <xref:System.Collections.Generic.Stack%601> collection. Sur les grandes collections qui sont fréquemment, les performances de cet exemple sera considérablement plus grande que l’exemple précédent.

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

[Génériques](../windows/generics-cpp-component-extensions.md)