---
description: 'En savoir plus sur : erreur du compilateur C2645'
title: Erreur du compilateur C2645
ms.date: 11/04/2016
f1_keywords:
- C2645
helpviewer_keywords:
- C2645
ms.assetid: 6609c2fa-c3b2-4a6b-8e8d-58fb52f67175
ms.openlocfilehash: d757b171fd314a5ed90fafe76d1b45074ec5b604
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160829"
---
# <a name="compiler-error-c2645"></a>Erreur du compilateur C2645

aucun nom qualifié pour un pointeur vers un membre (trouvé' :: * ')

La déclaration d’un pointeur vers un membre ne spécifie pas de classe.

L’exemple suivant génère l’C2645 :

```cpp
// C2645.cpp
class A {};
int main() {
   int B::* bp;   // C2645 B not defined
   int A::* ap;   // OK
}
```
