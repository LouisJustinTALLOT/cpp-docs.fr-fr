---
title: Erreur du compilateur C2780
ms.date: 11/04/2016
f1_keywords:
- C2780
helpviewer_keywords:
- C2780
ms.assetid: 423793d8-a3b2-4f35-85f8-ae1d043e2b69
ms.openlocfilehash: 9a427bbd79570a2646447d5326e034035306fac6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257450"
---
# <a name="compiler-error-c2780"></a>Erreur du compilateur C2780

'déclaration' : N arguments attendus - M fournis

Un modèle de fonction a trop peu d’arguments ou trop d’arguments.

L'exemple suivant génère l'erreur C2780 et montre comment la corriger :

```
// C2780.cpp
template<typename T>
void f(T, T){}

int main() {
   f(1);  // C2780
   // try the following line instead
   // f(1,2);
}
```