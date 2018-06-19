---
title: Erreur du compilateur C3149 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3149
dev_langs:
- C++
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c0441a7aebf86139aedbd5e45a7645db0a90b37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248506"
---
# <a name="compiler-error-c3149"></a>Erreur du compilateur C3149
'type' : Impossible d’utiliser ce type ici sans un niveau supérieur 'char'  
  
 Une déclaration n’a pas été spécifiée correctement.  
  
 Par exemple, peut avoir défini un type CLR dans une portée globale et tenté de créer une variable du type dans le cadre de la définition. Étant donné que les variables globales de types CLR ne sont pas autorisées, le compilateur génère l’erreur C3149.  
  
 Pour résoudre cette erreur, déclarez les variables des types CLR à l’intérieur d’une définition de fonction ou type.  
  
 L’exemple suivant génère l’erreur C3149 :  
  
```  
// C3149.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   // declare an array of value types   
   array< Int32 ^> IntArray;   // C3149  
   array< Int32>^ IntArray2;   // OK  
}  
```  
  
 L’exemple suivant génère l’erreur C3149 :  
  
```  
// C3149b.cpp  
// compile with: /clr /c  
delegate int MyDelegate(const int, int);  
void Test1(MyDelegate m) {}   // C3149  
void Test2(MyDelegate ^ m) {}   // OK  
```  
