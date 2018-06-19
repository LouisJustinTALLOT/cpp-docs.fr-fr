---
title: Erreur du compilateur C2663 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f39f516b32aaf1159d47726d01623e253ee8b383
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235857"
---
# <a name="compiler-error-c2663"></a>Erreur du compilateur C2663
'fonction' : nombre surcharges n’ont pas de conversion autorisée pour le pointeur 'this'  
  
 Le compilateur n’a pas pu convertir `this` à une des versions surchargées de la fonction membre.  
  
 Cette erreur peut être provoquée en appelant un non -`const` fonction membre sur une `const` objet.  Solutions possibles :  
  
1.  Supprimer le `const` à partir de la déclaration d’objet.  
  
2.  Ajouter `const` à une des surcharges de fonction membre.  
  
 L’exemple suivant génère l’erreur C2663 :  
  
```  
// C2663.cpp  
struct C {  
   void f() volatile {}  
   void f() {}  
};  
  
struct D {  
   void f() volatile;  
   void f() const {}  
};  
  
const C *pcc;  
const D *pcd;  
  
int main() {  
   pcc->f();    // C2663  
   pcd->f();    // OK  
}  
```