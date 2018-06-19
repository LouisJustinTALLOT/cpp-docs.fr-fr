---
title: Erreur du compilateur C3392 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3392
dev_langs:
- C++
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e31c2b46c8b2688053bf02f40a2de6629632dd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251034"
---
# <a name="compiler-error-c3392"></a>Erreur du compilateur C3392
'arg_type' : argument de type non valide pour le paramètre générique 'param' du générique 'type-générique', doit posséder un constructeur sans paramètre public  
  
 Un type générique a été instancié de manière incorrecte. Vérifiez la définition du type. Pour plus d’informations, consultez [génériques](../../windows/generics-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
L’exemple suivant utilise c# pour créer un composant qui contient un type générique qui a certaines contraintes qui ne sont pas pris en charge lors de la création de types génériques dans le langage c++ / CLI. Pour plus d’informations, consultez [Contraintes sur les paramètres de type](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).  
  
```cs  
// C3392.cs  
// Compile by using: csc /target:library C3392.cs  
// a C# program  
public class GR<C, V, N>  
where C : class  
where V : struct  
where N : new() {}  
```  
  
Lorsque le composant C3392.dll est disponible, l’exemple suivant génère l’erreur C3392.  
  
```cpp  
// C3392_b.cpp  
// Compile by using: cl /clr C3392_b.cpp  
#using <C3392.dll>  
  
ref class R { R(int) {} };  
ref class N { N() {} };  
  
value class V {};  
  
ref class N2 { public: N2() {} };  
ref class R2 { public: R2() {} };  
  
int main () {  
   GR<R^, V, N^>^ gr1;   // C3392  
   GR<R^, V, N2^>^ gr1a; // OK  
  
   GR<R^, N^, N^>^ gr3;  // C3392  
   GR<R^, V, N2^>^ gr3a; // OK  
  
   GR<R^, V, R^>^ gr4;   // C3392  
   GR<R^, V, R2^>^ gr4a; // OK  
}  
```