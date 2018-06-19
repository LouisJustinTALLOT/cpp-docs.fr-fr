---
title: 'Comment : améliorer les performances avec des génériques (Visual C++) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- performance, C++
- Visual C++, performance
- Visual C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da74cce5f41c3399fb102180cfdfe8c1215c8bf9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877564"
---
# <a name="how-to-improve-performance-with-generics-visual-c"></a>Comment : améliorer les performances avec des génériques (Visual C++)
Avec les génériques, vous pouvez créer du code réutilisable basé sur un paramètre de type. Le type réel du paramètre de type est différé jusqu'à ce que l’appelé par le code client. Pour plus d’informations sur les types génériques, consultez [génériques](../windows/generics-cpp-component-extensions.md).  
  
 Cet article explique comment génériques peuvent aider à améliorer les performances d’une application qui utilise les collections.  
  
## <a name="example"></a>Exemple  
 Le .NET Framework est fourni avec nombreuses classes de collection dans le <xref:System.Collections?displayProperty=fullName> espace de noms. La plupart de ces collections opèrent sur des objets de type <xref:System.Object?displayProperty=fullName>. Cela permet de collections pour stocker n’importe quel type, étant donné que tous les types dans le .NET Framework, même les types valeur, dérivent de <xref:System.Object?displayProperty=fullName>. Toutefois, il existe deux inconvénients à cette approche.  
  
 Tout d’abord, si la collection est le stockage des types valeur tels que les entiers, la valeur doit être convertie (boxed) avant d’être ajouté à la collection et unboxed lorsque la valeur est récupérée à partir de la collection. Il s’agit des opérations coûteuses.  
  
 En second lieu, il n’existe aucun moyen de contrôler les types peuvent être ajoutés à une collection. Il est parfaitement conforme pour ajouter un nombre entier et une chaîne à la même collection, même si cela est probablement pas ce qui a été conçu. Par conséquent, dans l’ordre pour que votre code soit de type sécurisé, vous devez vérifier que le type de récupérer de la collection est vraiment ce qui était attendu.  
  
 L’exemple de code suivant montre les deux principaux inconvénients des regroupements avant les génériques .NET Framework.  
  
```  
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
 La nouvelle <xref:System.Collections.Generic?displayProperty=fullName> espace de noms contient de nombreux regroupements mêmes trouvés dans le <xref:System.Collections?displayProperty=fullName> espace de noms, mais ils ont été modifiés pour accepter les paramètres de type générique. Cela élimine les deux inconvénients de collections non génériques : la conversion boxing et unboxing de types valeur et l’impossibilité de spécifier les types à stocker dans les collections. Opérations sur les deux collections sont identiques ; ils diffèrent uniquement dans la manière dont ils sont instanciés.  
  
 Comparez l’exemple suivant écrit ci-dessus avec cet exemple qui utilise un type générique <xref:System.Collections.Generic.Stack%601> collection. Les regroupements volumineux qui sont fréquemment, les performances de cet exemple sera considérablement supérieure à l’exemple précédent.  
  
```  
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