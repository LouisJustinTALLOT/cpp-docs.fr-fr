---
title: Erreur du compilateur C2774 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2774
dev_langs:
- C++
helpviewer_keywords:
- C2774
ms.assetid: 10f428c6-7f49-489a-92ba-6ef978b7caaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 500dc43dbc4e8d3c5768c6cc71226e5f1025564a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110469"
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