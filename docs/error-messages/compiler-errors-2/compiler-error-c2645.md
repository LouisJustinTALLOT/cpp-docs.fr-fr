---
title: Erreur du compilateur C2645
ms.date: 11/04/2016
f1_keywords:
- C2645
helpviewer_keywords:
- C2645
ms.assetid: 6609c2fa-c3b2-4a6b-8e8d-58fb52f67175
ms.openlocfilehash: 9df9f41da3d4cbef97511b979845c5a6b404614b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152590"
---
# <a name="compiler-error-c2645"></a>Erreur du compilateur C2645

Aucun nom qualifié pour un pointeur vers membre (trouvé ' :: *')

La déclaration d’un pointeur vers un membre ne spécifie pas une classe.

L’exemple suivant génère l’erreur C2645 :

```
// C2645.cpp
class A {};
int main() {
   int B::* bp;   // C2645 B not defined
   int A::* ap;   // OK
}
```