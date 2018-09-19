---
title: Erreur du compilateur C2775 | Microsoft Docs
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
ms.openlocfilehash: 4c5a3031fede7b2f47510f80eba09f62a06343f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045833"
---
# <a name="compiler-error-c2775"></a>Erreur du compilateur C2775

'identificateur' : aucune méthode 'get' n’est associé à cette propriété

Un membre de données déclaré avec le [propriété](../../cpp/property-cpp.md) étendue d’attribut n’est pas un `get` fonction spécifiée, mais une expression tente de récupérer sa valeur.

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