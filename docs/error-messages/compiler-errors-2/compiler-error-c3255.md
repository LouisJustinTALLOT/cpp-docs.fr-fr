---
title: Erreur du compilateur C3255 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3255
dev_langs:
- C++
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 740deb9a2981839a12d2570328369daf741a8da9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251593"
---
# <a name="compiler-error-c3255"></a>Erreur du compilateur C3255
'type valeur' : Impossible d’allouer dynamiquement cet objet de type valeur sur un tas natif  
  
 Les instances d’un type valeur (voir [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md)) qui contient des membres managés peuvent être créées sur la pile, mais pas sur le tas.  
  
 L’exemple suivant génère l’erreur C3255 :  
  
```  
// C3255.cpp  
// compile with: /clr  
using namespace System;  
value struct V {  
   Object^ o;  
};  
  
value struct V2 {  
   int i;  
};  
  
int main() {  
   V* pv = new V;   // C3255  
   V2* pv2 = new V2;  
   V v2;  
}  
```  
