---
title: 'Comment : consommer un indexeur c# (C + c++ / CLI) | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++, indexers
- indexers, consuming C#
ms.assetid: 5a11850c-a1a2-4a0a-b95e-f6dc5a87f439
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 00a8164b91a4e483330d4969325a7bd4b6fe6e6a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127404"
---
# <a name="how-to-consume-a-c-indexer-ccli"></a>Comment : consommer un indexeur C# (C++/CLI)
Visual C++ ne contient pas d’indexeur ; Il possède des propriétés indexées. Pour consommer un indexeur c#, accédez à l’indexeur comme s’il s’agissait d’une propriété indexée.  
  
 Pour plus d’informations à propos des indexeurs, consultez :  
  
-   [Indexeurs](/dotnet/csharp/programming-guide/indexers/index)  
  
## <a name="example"></a>Exemple  
 L’exemple de programme c# suivant définit un indexeur.  
  
```  
// consume_cs_indexers.cs  
// compile with: /target:library  
using System;  
public class IndexerClass {  
   private int [] myArray = new int[100];   
   public int this [int index] {   // Indexer declaration  
      get {  
         // Check the index limits.  
         if (index < 0 || index >= 100)  
            return 0;  
         else  
            return myArray[index];  
      }  
      set {  
         if (!(index < 0 || index >= 100))  
            myArray[index] = value;  
      }  
   }  
}  
/*  
// code to consume the indexer  
public class MainClass {  
   public static void Main() {  
      IndexerClass b = new IndexerClass();  
  
      // Call indexer to initialize elements 3 and 5  
      b[3] = 256;  
      b[5] = 1024;  
      for (int i = 0 ; i <= 10 ; i++)   
         Console.WriteLine("Element #{0} = {1}", i, b[i]);  
   }  
}  
*/  
```  
  
## <a name="example"></a>Exemple  
 Ce programme Visual C++ utilise l’indexeur.  
  
```  
// consume_cs_indexers_2.cpp  
// compile with: /clr  
#using "consume_cs_indexers.dll"  
using namespace System;  
  
int main() {  
   IndexerClass ^ ic = gcnew IndexerClass;  
   ic->default[0] = 21;  
   for (int i = 0 ; i <= 10 ; i++)  
      Console::WriteLine("Element #{0} = {1}", i, ic->default[i]);  
}  
```  
  
```Output  
Element #0 = 21  
Element #1 = 0  
Element #2 = 0  
Element #3 = 0  
Element #4 = 0  
Element #5 = 0  
Element #6 = 0  
Element #7 = 0  
Element #8 = 0  
Element #9 = 0  
Element #10 = 0  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interopérabilité avec d’autres langages .NET (C++-CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)