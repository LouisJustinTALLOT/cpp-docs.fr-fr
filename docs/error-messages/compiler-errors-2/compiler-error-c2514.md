---
description: 'En savoir plus sur : erreur du compilateur C2514'
title: Erreur du compilateur C2514
ms.date: 11/04/2016
f1_keywords:
- C2514
helpviewer_keywords:
- C2514
ms.assetid: 4b7085e5-6714-4261-80b7-bc72e64ab3e8
ms.openlocfilehash: 3999a5a65df08142b68e7257b257d39d1b5245e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212816"
---
# <a name="compiler-error-c2514"></a>Erreur du compilateur C2514

'classe' : la classe n’a aucun constructeur

La classe, la structure ou l’Union n’a aucun constructeur avec une liste de paramètres qui correspond aux paramètres utilisés pour l’instancier.

Une classe doit être entièrement déclarée avant de pouvoir être instanciée.

L’exemple suivant génère l’C2514 :

```cpp
// C2514.cpp
// compile with: /c
class f;

class g {
public:
    g (int x);
};

class fmaker {
   f *func1() {
      return new f(2);   // C2514
   }

   g *func2() {
      return new g(2);   // OK
   }
};
```
