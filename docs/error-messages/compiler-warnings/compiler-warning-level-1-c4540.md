---
title: Compilateur avertissement (niveau 1) C4540 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3939ad2bbcba1ab3b492d83bdbb8f7076c2c5f2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283060"
---
# <a name="compiler-warning-level-1-c4540"></a>Avertissement du compilateur (niveau 1) C4540
utilisé de dynamic_cast pour convertir une base ambiguë ou inaccessible ; test d’exécution échouera ('type1' en 'type2')  
  
 Vous avez utilisé `dynamic_cast` convertir d’un type à un autre. Le compilateur a déterminé que le cast échouerait toujours (retourner **NULL**) parce qu’une classe de base est inaccessible (`private`, par exemple) ou ambiguë (apparaît plusieurs fois dans la hiérarchie de classes, par exemple).  
  
 Voici un exemple de cet avertissement. Classe **B** est dérivé de la classe **A**. Le programme utilise `dynamic_cast` pour effectuer un cast à partir de la classe **B** (la classe dérivée) pour la classe **A**, qui continue d’échouer, car classe **B** est `private` et par conséquent inaccessible. Modification d’accès de **A** à **public** résout l’avertissement.  
  
```  
// C4540.cpp  
// compile with: /W1  
  
struct A {   
   virtual void g() {}  
};  
  
struct B : private A {  
   virtual void g() {}  
};  
  
int main() {  
   B b;  
   A * ap = dynamic_cast<A*>(&b);   // C4540  
}  
```