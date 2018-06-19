---
title: Erreur du compilateur C2555 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2d1a710177e2c8c72b0afeff662dddf1c22ef5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230582"
---
# <a name="compiler-error-c2555"></a>Erreur du compilateur C2555
'classe1::fonction1' : fonction virtuelle de substitution type de retour est différent et n’est pas covariant 'classe2::fonction2'  
  
 Une fonction virtuelle et une fonction de substitution dérivée ont des listes de paramètres sont identiques, mais différents types de retournés. Une fonction de substitution dans une classe dérivée ne peuvent pas différer d’une fonction virtuelle dans une classe de base uniquement par son type de retour.  
  
 Pour résoudre cette erreur, effectuez un cast de la valeur de retour après la fonction virtuelle a été appelé.  
  
 Vous pouvez également voir cette erreur si vous compilez avec/CLR.   Par exemple, Visual C++ équivalent à la déclaration c# suivante :  
  
```  
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);  
```  
  
 est  
  
```  
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];  
```  
  
 Pour plus d’informations sur l’erreur C2555, consultez l’article Q240862 de la Base de connaissances Microsoft.  
  
 L’exemple suivant génère l’erreur C2555 :  
  
```  
// C2555.cpp  
// compile with: /c  
struct X {  
   virtual void func();  
};  
struct Y : X {  
   char func();  // C2555  
   void func2();   // OK  
};  
```