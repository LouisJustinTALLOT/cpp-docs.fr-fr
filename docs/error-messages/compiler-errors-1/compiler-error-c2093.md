---
title: Erreur du compilateur C2093
ms.date: 11/04/2016
f1_keywords:
- C2093
helpviewer_keywords:
- C2093
ms.assetid: 17529a70-9169-46b5-9fc6-57a5ce224e6a
ms.openlocfilehash: d57b452e63f7bf76051ef6a23c5f8f6ba81aed1e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511148"
---
# <a name="compiler-error-c2093"></a>Erreur du compilateur C2093

'variable1' : ne peut pas être initialisée à l’aide de l’adresse de la variable automatique 'variable2'

Lors de la compilation avec [/Za](../../build/reference/za-ze-disable-language-extensions.md), le programme a tenté d’utiliser l’adresse d’une variable automatique comme initialiseur.

L’exemple suivant génère l’erreur C2093 :

```
// C2093.c
// compile with: /Za /c
void func() {
   int li;   // an implicit auto variable
   int * s[]= { &li };   // C2093 address is not a constant

   // OK
   static int li2;
   int * s2[]= { &li2 };
}
```