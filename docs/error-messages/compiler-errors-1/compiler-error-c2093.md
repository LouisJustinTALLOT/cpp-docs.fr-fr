---
title: Erreur du compilateur C2093 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2093
dev_langs:
- C++
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11419a7df335bd87077759228be1256c92d09caa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170711"
---
# <a name="compiler-error-c2093"></a>Erreur du compilateur C2093
'variable1' : ne peut pas être initialisée à l’aide de l’adresse de la variable automatique 'variable2'  
  
 Lors de la compilation avec [/Za](../../build/reference/za-ze-disable-language-extensions.md), le programme a tenté d’utiliser l’adresse d’une variable automatique comme initialiseur.  
  
 L’exemple suivant génère l’erreur C2093 :  
  
```  
// C2093.c  
// compile with: /Za /c  
void func() {  
   int li;   // an implicit auto variable  
   int * s[]= { &li };   // C2093 address is not a constant  
  
   // OK  
   static int li2;  
   int * s2[]= { &li2 };  
}  
```