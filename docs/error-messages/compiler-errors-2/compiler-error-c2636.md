---
description: 'En savoir plus sur : erreur du compilateur C2636'
title: Erreur du compilateur C2636
ms.date: 11/04/2016
f1_keywords:
- C2636
helpviewer_keywords:
- C2636
ms.assetid: 379873ec-8d05-49f8-adf1-b067bc07bdb8
ms.openlocfilehash: 789da819b85435bfb54d0f88c6e6c1414f04b6f0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208734"
---
# <a name="compiler-error-c2636"></a>Erreur du compilateur C2636

'identificateur' : pointeur non conforme vers un membre de référence

Un pointeur vers un membre de référence a été déclaré.

L’exemple suivant génère l’C2636 :

```cpp
// C2636.cpp
struct S {};
int main() {
   int &S::*prs;   // C2636
   int S::*prs1;   // OK
   int *S::*prs2;   // OK
}
```
