---
title: Erreur du compilateur C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: f18819e5f078cb85121160af1d4a3fc24a365a68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615187"
---
# <a name="compiler-error-c2601"></a>Erreur du compilateur C2601

'fonction' : les définitions de fonction locale ne sont pas conformes

Code tente de définir une fonction dans une fonction.

Ou bien, il peut y avoir une accolade supplémentaire dans votre code source avant de l’emplacement de l’erreur C2601.

L’exemple suivant génère l’erreur C2601 :

```
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```