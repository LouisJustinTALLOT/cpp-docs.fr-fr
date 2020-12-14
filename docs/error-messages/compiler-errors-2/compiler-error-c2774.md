---
description: 'En savoir plus sur : erreur du compilateur C2774'
title: Erreur du compilateur C2774
ms.date: 11/04/2016
f1_keywords:
- C2774
helpviewer_keywords:
- C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
ms.openlocfilehash: d934b2f85fe571c43c8db69018c7c13fd782226a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298199"
---
# <a name="compiler-error-c2774"></a>Erreur du compilateur C2774

'identificateur' : aucune méthode’put’associée à cette propriété

Un membre de données déclaré avec la [propriété](../../cpp/property-cpp.md) n’a aucune `put` fonction, mais une expression tente de définir sa valeur.

L’exemple suivant génère l’C2774 :

```cpp
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
