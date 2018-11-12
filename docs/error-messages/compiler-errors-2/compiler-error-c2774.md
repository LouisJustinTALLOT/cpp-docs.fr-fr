---
title: Erreur du compilateur C2774
ms.date: 11/04/2016
f1_keywords:
- C2774
helpviewer_keywords:
- C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
ms.openlocfilehash: 6197e3da81a9f059c90d15608a939ad4887e526d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586886"
---
# <a name="compiler-error-c2774"></a>Erreur du compilateur C2774

'identificateur' : aucune méthode 'put' n’est associé à cette propriété

Une donnée membre déclarée avec [propriété](../../cpp/property-cpp.md) n’a aucun `put` (fonction), mais une expression tente de définir sa valeur.

L’exemple suivant génère l’erreur C2774 :

```
// C2774.cpp
struct A {
   __declspec(property(get=GetProp)) int prop;
   int GetProp(void);

   __declspec(property(get=GetProp2, put=PutProp2)) int prop2;
   int GetProp2(void);
   void PutProp2(int);
};

int main() {
   A* pa = new A;
   int val = 0;
   pa->prop = val;   // C2774
   pa->prop++;   // C2774
}
```