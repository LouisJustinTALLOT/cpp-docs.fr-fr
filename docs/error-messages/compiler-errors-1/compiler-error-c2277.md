---
description: 'En savoir plus sur : erreur du compilateur C2277'
title: Erreur du compilateur C2277
ms.date: 11/04/2016
f1_keywords:
- C2277
helpviewer_keywords:
- C2277
ms.assetid: 15a83b07-8731-4524-810b-267f65a7844f
ms.openlocfilehash: e5113587b22373eae4a197b5913430659447810a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344430"
---
# <a name="compiler-error-c2277"></a>Erreur du compilateur C2277

'identificateur' : impossible de prendre l’adresse de cette fonction membre

Vous ne pouvez pas prendre l’adresse d’une fonction membre.

L’exemple suivant génère l’C2277 :

```cpp
// C2277.cpp
class A {
public:
   A();
};
(*pctor)() = &A::A;   // C2277
```
