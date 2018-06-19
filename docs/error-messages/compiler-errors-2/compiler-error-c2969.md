---
title: Erreur du compilateur C2969 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2969
dev_langs:
- C++
helpviewer_keywords:
- C2969
ms.assetid: e4ea3d66-b937-4b2c-b42a-96e03fb11579
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef2cbaa434ec535dd90026ee6549b15f700bf9d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33241897"
---
# <a name="compiler-error-c2969"></a>Erreur du compilateur C2969
erreur de syntaxe : 'symbole' : la définition d’une fonction membre doit se terminer par '}'  
  
 Une définition de fonction membre de modèle contient une accolade fermante non appariée.  
  
 L’exemple suivant génère l’erreur C2969 :  
  
```  
// C2969.cpp  
// compile with: /c  
class A {  
   int i;  
public:  
   A(int i) {}  
};  
  
A anA(1);  
  
class B {  
   A a;  
   B() : a(anA);   // C2969  
   // try the following line instead  
   // B() : a(anA) {}  
};  
```