---
title: Erreur du compilateur C3254 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3254
dev_langs:
- C++
helpviewer_keywords:
- C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e58976b1562e6cca9aa343401b5d2c3f856de1a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255606"
---
# <a name="compiler-error-c3254"></a>Erreur du compilateur C3254
'substitution explicite' : classe contient une substitution explicite 'substitution', mais ne dérive pas d’une interface qui contient la déclaration de fonction  
  
 Lorsque vous [substituer explicitement](../../cpp/explicit-overrides-cpp.md) une méthode, la classe qui contient la substitution doit provenir directement ou indirectement, à partir du type qui contient la fonction que vous substituez.  
  
 L’exemple suivant génère l’erreur C3254 :  
  
```  
// C3254.cpp  
__interface I  
{  
   void f();  
};  
  
__interface I1 : I  
{  
};  
  
struct A /* : I1 */  
{  
   void I1::f()  
   {   // C3254, uncomment : I1 to resolve this C3254  
   }  
};  
  
int main()  
{  
}  
```