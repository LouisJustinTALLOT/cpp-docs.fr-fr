---
description: 'En savoir plus sur : erreur du compilateur C3230'
title: Erreur du compilateur C3230
ms.date: 11/04/2016
f1_keywords:
- C3230
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
ms.openlocfilehash: dfd14d11b18c7398ef5881ebe8935e0cf6c302cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272407"
---
# <a name="compiler-error-c3230"></a>Erreur du compilateur C3230

'fonction' : l’argument de type de modèle de 'modèle' ne peut pas contenir de paramètre de type générique : 'paramètre'

Les modèles sont instanciés au moment de la compilation, mais les génériques sont instanciés au moment de l’exécution. Ainsi, il n’est pas possible de générer du code générique pouvant appeler le modèle, car celui-ci ne peut pas être instancié au moment de l’exécution quand le type générique est enfin connu.

L’exemple suivant génère l’erreur C3230 :

```cpp
// C3230.cpp
// compile with: /clr /LD
template <class S>
void f(S t);

generic <class U>
ref class C {
   void f1(U x) {
      f(x);   // C3230
   }
};
```
