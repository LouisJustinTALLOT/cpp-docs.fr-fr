---
title: "Erreur du compilateur C3287 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3287"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3287"
ms.assetid: c1fa73d2-2c82-4136-a7da-0e75e3b420ad
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur du compilateur C3287
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

le type 'type' \(type de retour de GetEnumerator\) doit avoir une fonction membre publique appropriée MoveNext et une propriété publique Current  
  
 Les classes de collection définies par l’utilisateur doivent contenir des définitions pour `MoveNext` et `Current`.  
  
 Pour plus d'informations, voir [Comment : itérer au sein d'une collection définie par l'utilisateur en utilisant for each](../../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md).  
  
## Exemple  
 L’exemple suivant génère l’erreur C3287.  
  
```  
// C3287.cpp // compile with: /clr using namespace System; ref struct R { bool MoveNext() { return true; } property Object^ Current { Object^ get() { Object ^ o = gcnew Object; return o; } } }; ref struct R2 { R ^GetEnumerator() { R^ r = gcnew R; return r; } }; ref struct T {}; ref struct T2 { T ^GetEnumerator() { T^ t = gcnew T; return t; } }; int main() { for each (int i in gcnew T2) {}   // C3287 for each (int i in gcnew R2) {}   // OK }  
```