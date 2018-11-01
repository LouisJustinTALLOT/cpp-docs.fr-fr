---
title: Erreur du compilateur C2088
ms.date: 11/04/2016
f1_keywords:
- C2088
helpviewer_keywords:
- C2088
ms.assetid: b93f7094-185b-423d-8bb9-507cd757dbf5
ms.openlocfilehash: 6d53f2896fc3b964a4d2652b3bfd0dcebb4a7226
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550773"
---
# <a name="compiler-error-c2088"></a>Erreur du compilateur C2088

'opérateur' : non conforme de 'clé-classe'

L’opérateur n’était pas défini pour la structure ou union. Cette erreur est uniquement valide pour le code C.

L’exemple suivant génère les trois fois C2088 :

```
// C2088.c
struct S {
   int m_i;
} s;

int main() {
   int i = s * 1;   // C2088
   struct S s2 = +s;   // C2088
   s++;   // C2088
}
```