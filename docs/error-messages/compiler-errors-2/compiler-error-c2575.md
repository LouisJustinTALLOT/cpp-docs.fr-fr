---
description: 'En savoir plus sur : erreur du compilateur C2575'
title: Erreur du compilateur C2575
ms.date: 11/04/2016
f1_keywords:
- C2575
helpviewer_keywords:
- C2575
ms.assetid: 9eb45706-37ef-4481-b373-6d193ba13634
ms.openlocfilehash: c08404ec3ce2d260d19b9889b668c0d98db265b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208877"
---
# <a name="compiler-error-c2575"></a>Erreur du compilateur C2575

'identificateur' : seules les fonctions membres et les bases peuvent être virtuelles

Une fonction ou une classe globale est déclarée **`virtual`** . Cette opération n’est pas autorisée.

L’exemple suivant génère l’C2575 :

```cpp
// C2575.cpp
// compile with: /c
virtual void func() {}   // C2575

void func2() {}
struct A {
   virtual void func2(){}
};
```
