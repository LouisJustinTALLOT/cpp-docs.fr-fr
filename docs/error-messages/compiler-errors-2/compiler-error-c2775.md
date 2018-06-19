---
title: Erreur du compilateur C2775 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2775
dev_langs:
- C++
helpviewer_keywords:
- C2775
ms.assetid: 9c488508-ade0-48f1-b94f-d538d15f807a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29db1a183af3c19a21cb1ea6ca677c3741a67ddf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235374"
---
# <a name="compiler-error-c2775"></a>Erreur du compilateur C2775
'identificateur' : aucune méthode 'get' n’est associé à cette propriété.  
  
 Une donnée membre déclarée avec le [propriété](../../cpp/property-cpp.md) étendue d’attribut n’est pas un `get` fonction spécifiée, mais une expression tente de récupérer sa valeur.  
  
 L’exemple suivant génère l’erreur C2775 :  
  
```  
// C2775.cpp  
struct A {  
   __declspec(property(put=PutProp2, get=GetProp2)) int prop2;  
   int GetProp2(){return 0;}  
   void PutProp2(int){}  
  
   __declspec(property(put=PutProp)) int prop;  
   int PutProp(void){}  
  
};  
  
int main() {  
   A* pa = new A;  
   int x;  
   x = pa->prop;   // C2775  
   x = pa->prop2;  
}  
```