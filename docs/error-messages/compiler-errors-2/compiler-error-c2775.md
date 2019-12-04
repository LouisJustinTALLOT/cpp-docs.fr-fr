---
title: Erreur du compilateur C2775
ms.date: 11/04/2016
f1_keywords:
- C2775
helpviewer_keywords:
- C2775
ms.assetid: 9c488508-ade0-48f1-b94f-d538d15f807a
ms.openlocfilehash: be858c7508aa520f78ec144b02738af02099b49b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740050"
---
# <a name="compiler-error-c2775"></a>Erreur du compilateur C2775

'identificateur' : aucune méthode’obtient’n’est associée à cette propriété

Un membre de données déclaré avec l’attribut étendu de [propriété](../../cpp/property-cpp.md) n’a pas de fonction `get` spécifiée, mais une expression tente de récupérer sa valeur.

L’exemple suivant génère l’C2775 :

```cpp
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
