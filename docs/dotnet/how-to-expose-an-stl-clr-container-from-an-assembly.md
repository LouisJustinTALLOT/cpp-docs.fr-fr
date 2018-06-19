---
title: 'Comment : exposer un conteneur STL/CLR à partir d’un Assembly | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 58edb96d3947cc5694731d78c6aa71a855ef7aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33140171"
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>Comment : exposer un conteneur STL/CLR d'un assembly
Les conteneurs STL/CLR tels que `list` et `map` sont implémentés en tant que classes ref de modèle. Étant donné que les modèles C++ sont instanciés au moment de la compilation, deux classes de modèles qui ont exactement la même signature, mais se trouvent dans des assemblys différents sont réellement différents types. Cela signifie que les classes de modèle ne peut pas être utilisés au-delà des limites d’assembly.  
  
 Pour faire inter-assembly de partage, les conteneurs STL/CLR implémentent l’interface générique <xref:System.Collections.Generic.ICollection%601>. À l’aide de cette interface générique, tous les langages qui prennent en charge des génériques, y compris C++, c# et Visual Basic, peuvent accéder à des conteneurs STL/CLR.  
  
 Cette rubrique vous montre comment afficher les éléments de plusieurs conteneurs STL/CLR sont écrites dans un assembly C++ nommé `StlClrClassLibrary`. Nous allons montrer deux assemblys d’accéder à `StlClrClassLibrary`. Le premier assembly est écrite en C++ et la seconde en c#.  
  
 Si les deux assemblys sont écrits en C++, vous pouvez accéder à l’interface générique d’un conteneur à l’aide de son `generic_container` typedef. Par exemple, si vous avez un conteneur de type `cliext::vector<int>`, son interface générique est : `cliext::vector<int>::generic_container`. De même, vous pouvez obtenir un itérateur sur l’interface générique à l’aide de la `generic_iterator` typedef, comme dans : `cliext::vector<int>::generic_iterator`.  
  
 Étant donné que ces typedefs sont déclarés dans les fichiers d’en-tête C++, les assemblys écrits dans d’autres langues ne peut pas utiliser. Par conséquent, accéder à l’interface générique pour `cliext::vector<int>` dans c# ou tout autre langage .NET, utilisez `System.Collections.Generic.ICollection<int>`. Pour effectuer une itération au sein de cette collection, utilisez un `foreach` boucle.  
  
 Le tableau suivant répertorie chaque conteneur STL/CLR implémente l’interface générique :  
  
|Conteneur STL/CLR|Interface générique|  
|------------------------|-----------------------|  
|deque < T\>|ICollection < T\>|  
|hash_map < K, V >|IDictionary < K, V >|  
|hash_multimap < K, V >|IDictionary < K, V >|  
|hash_multiset < T\>|ICollection < T\>|  
|hash_set < T\>|ICollection < T\>|  
|liste < T\>|ICollection < T\>|  
|carte < K, V >|IDictionary < K, V >|  
|multimap < K, V >|IDictionary < K, V >|  
|multiset < T\>|ICollection < T\>|  
|définir < T\>|ICollection < T\>|  
|Vector < T\>|ICollection < T\>|  
  
> [!NOTE]
>  Étant donné que la `queue`, `priority_queue`, et `stack` conteneurs ne prennent pas en charge les itérateurs, ils n’implémentent pas d’interfaces génériques et ne peut pas être l’objet d’un accès inter-assembly.  
  
## <a name="example-1"></a>Exemple 1  
  
### <a name="description"></a>Description  
 Dans cet exemple, nous déclarer une classe C++ qui contient des données de membre privées STL/CLR. Nous avons ensuite déclarer des méthodes publiques pour accorder l’accès à des collections privées de la classe. Nous faisons de deux manières différentes, une pour les clients C++ et un pour les autres clients .NET.  
  
### <a name="code"></a>Code  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="example-2"></a>Exemple 2  
  
### <a name="description"></a>Description  
 Dans cet exemple, nous implémenter la classe déclarée dans l’exemple 1. Pour que les clients à utiliser cette bibliothèque de classes, nous utilisons l’outil manifeste **mt.exe** pour incorporer le fichier manifeste dans la DLL. Pour plus d’informations, consultez les commentaires de code.  
  
 Pour plus d’informations sur l’outil manifeste et les assemblys côte à côte, consultez [génération d’Applications isolées C/C++ et les assemblys côte à côte](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md).  
  
### <a name="code"></a>Code  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## <a name="example-3"></a>Exemple 3  
  
### <a name="description"></a>Description  
 Dans cet exemple, nous créer un client C++ qui utilise la bibliothèque de classes créée dans les exemples 1 et 2. Ce client utilise le `generic_container` typedefs des conteneurs STL/CLR pour itérer sur les conteneurs et leur contenu s’affiche.  
  
### <a name="code"></a>Code  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="output"></a>Sortie  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## <a name="example-4"></a>Exemple 4  
  
### <a name="description"></a>Description  
 Dans cet exemple, nous créer un client c# qui utilise la bibliothèque de classes créée dans les exemples 1 et 2. Ce client utilise le <xref:System.Collections.Generic.ICollection%601> méthodes des conteneurs STL/CLR pour itérer sur les conteneurs et leur contenu s’affiche.  
  
### <a name="code"></a>Code  
  
```  
// CsConsoleApp.cs  
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll  
  
using System;  
using System.Collections.Generic;  
using StlClrClassLibrary;  
using cliext;  
  
namespace CsConsoleApp  
{  
    class Program  
    {  
        static int Main(string[] args)  
        {  
            StlClrClass theClass = new StlClrClass();  
  
            Console.WriteLine("cliext::deque contents:");  
            ICollection<char> iCollChar = theClass.GetDequeCs();  
            foreach (char c in iCollChar)  
            {  
                Console.WriteLine(c);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::list contents:");  
            ICollection<float> iCollFloat = theClass.GetListCs();  
            foreach (float f in iCollFloat)  
            {  
                Console.WriteLine(f);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::map contents:");  
            IDictionary<int, string> iDict = theClass.GetMapCs();  
            foreach (KeyValuePair<int, string> kvp in iDict)  
            {  
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::set contents:");  
            ICollection<double> iCollDouble = theClass.GetSetCs();  
            foreach (double d in iCollDouble)  
            {  
                Console.WriteLine(d);  
            }  
            Console.WriteLine();  
  
            Console.WriteLine("cliext::vector contents:");  
            ICollection<int> iCollInt = theClass.GetVectorCs();  
            foreach (int i in iCollInt)  
            {  
                Console.WriteLine(i);  
            }  
            Console.WriteLine();  
  
            return 0;  
        }  
    }  
}  
```  
  
### <a name="output"></a>Sortie  
  
```  
cliext::deque contents:  
a  
b  
  
cliext::list contents:  
3.14159  
2.71828  
  
cliext::map contents:  
0 Hello  
1 World  
  
cliext::set contents:  
2.71828  
3.14159  
  
cliext::vector contents:  
10  
20  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)